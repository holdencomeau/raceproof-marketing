# Email Channel — Klaviyo State

**Status:** CANONICAL for email channel state.
**Last reviewed:** 2026-07-02
**PRD (implementation source of truth):** `raceproof-docs/planning/raceproof-klaviyo-implementation-prd.md`
**Related planning:** `raceproof-docs/planning/KLAVIYO_ACTIONABLE_TRIGGERS.md`, `raceproof-docs/planning/klaviyo-phase1-code-prompt.md`

---

## Account and identity

| Item | Value |
|---|---|
| Public site ID | `Ycv97d` |
| Identity resolution | `external_id` links Klaviyo profiles to Raceproof accounts |
| Image CDN pattern | `https://d3k81ch9hvuctc.cloudfront.net/company/Ycv97d/images/[uuid].png` (wordmark confirmed live) |
| Plan | Free plan. Klaviyo logo forced in email footer; removable only by upgrading. Profile limit is NOT the cause of silent sends (see lesson below). |
| MCP | Klaviyo MCP connector available for live verification (profiles, lists, flows, metrics). |

## Lists

| List | ID | Notes |
|---|---|---|
| Raceproof_Beta_Waitlist | `TzN2Ug` | Single opt-in, confirmed via API 2026-06-16 |
| Beta Approved | `UrY4Xu` | Triggers the beta invite flow |
| Invite to Discord | `UEmZZG` | |

## Pipeline wiring (live)

- Single registration path: `POST /beta-apply` (form at `raceproof.app/apply`) syncs the profile to Klaviyo on submission. The old `/beta-signup` waitlist route returns 410 Gone and its site forms are removed.
- `syncBetaProfile()` uses the **Subscribe Profiles** endpoint (fixed in raceproof-api `32810c6`), so every new profile lands with `SUBSCRIBED` consent. Verified live via Klaviyo MCP 2026-06-16 on the five most recent profiles.
- Historical applicants were bulk-imported from the `registrants` and `beta_signups` Postgres tables and consent-backfilled. Historical profiles do not need flow backfilling; they received welcome emails through another channel.

## The consent lesson (hard-won, do not relearn)

Klaviyo silently drops flow emails at the send step for any profile whose consent status is `NEVER_SUBSCRIBED`. Adding a profile to a list (Add Profile to List endpoint) does not subscribe it. When a flow shows eligible profiles but zero activity, verify subscription consent method via the API first. The free-plan profile limit was a wrong diagnosis once; do not reach for it again without evidence.

## Templates

Files live at `raceproof-docs/brand/Content Assets/Email/`.

| Template | Purpose |
|---|---|
| Letter | Workhorse for all founder-voice sends. White body, `#F5F5F5` gutter, `#0c0c0e` header/footer, 4px lime `#c4f04d` accent bar, Newsreader body, JetBrains Mono footer. No headings, no lists. |
| Data card | Letter frame plus a single image slot for Torque charts. |
| Beta welcome | Subject "Your beta access is live." Copy signed Holden. |
| Connected-source welcome | Triggered after a beta user connects a data source; brand-corrected rewrite 2026-06-17 (first person, no buttons, underlined text link, no title in sign-off, no "fingerprint"). |

**Template mechanics:** Klaviyo's HTML importer requires `{% unsubscribe %}` and `{% manage_preferences %}` as block tags (curly-percent). The double-brace variable form hard-fails validation. `{{ organization.name }}` and `{{ organization.address }}` resolve from account settings.

**Email brand rules:** first person from Holden, never "we" or "our team." Links are underlined text, never buttons. Sign-off is "Holden," no title. Lime reserved for the single action element. Monospace quarantined to footer/chrome. "Raceproof" lowercase p.

## Phase 2 (scoped, not shipped)

Task file: `KLAVIYO-PHASE2-001.md` (Code handoff, written 2026-06-16). Scope: `approve-beta-user.js` CLI, account creation and login hooks with `external_id` linkage, client-side `klaviyo.identify()` in the React app, `createEvent` in `klaviyo.js`, engagement event hooks (data source connections, PTA analysis). The PRD's event taxonomy and four-phase rollout plan govern.

## Operational notes

- Local script execution against Railway: skip `railway run` (injects unreachable `postgres.railway.internal`). Set `$env:DATABASE_URL`, `$env:KLAVIYO_PRIVATE_KEY`, `$env:KLAVIYO_BETA_LIST_ID` manually in PowerShell and run `node` directly.
- API scopes: consent operations need `subscriptions:write` on the private key.
