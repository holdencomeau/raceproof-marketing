# Social Channels — State and Production Recipes

**Status:** CANONICAL for social channel state.
**Last reviewed:** 2026-07-02
**Voice source of truth:** `raceproof-docs/brand/SOCIAL_MEDIA_VOICE_GUIDE.md` (read before drafting anything).

---

## Channel voices (summary; the guide governs)

| Channel | Voice | Rules |
|---|---|---|
| LinkedIn | Professional product voice | Flowing sentences with short reinforcement. "And the effect..." bridges data to meaning. No hashtags. LinkedIn deprioritizes external links: post without the URL, drop the link as a comment reply once the thread has engagement. |
| Instagram | Fast, visual-first | One contrast per post. Introduce concepts in natural language before product jargon. Hashtags for discovery. Link as quiet close ("link in bio"). Bio points at `raceproof.app/links`. |
| Strava | Personal athlete voice | First person, no hashtags, blog-length, use the title field. Images 1080x1350 (4:5 portrait). |
| Discord | Casual community announcement | First person, one discussion-seeding question, beta invitation stated once without selling language. Member-facing posts are never automated on a cadence. |
| All channels | | Specific numbers. No generic CTAs. No em dashes. Factual claims validated. |

## Distribution log

| Date | Article / campaign | Channels | Notes |
|---|---|---|---|
| 2026-06-12 | "Your FTP Is a Seat" | LinkedIn, Instagram, Strava, Discord | Two-beat LinkedIn strategy: bare analogy hook first ("Setting your FTP at 95% of your best 20 minute power is sort of like setting your max heart rate at 220 minus your age."), full article post as beat two. 6-slide IG carousel from four app screenshots. |
| 2026-07-02 | "The Number You Can't Name" | **Not recorded** | Confirm with Holden whether a distribution pass happened before drafting one. |

## Asset production recipes (proven in-session)

**Instagram carousel (1080x1350, 6 slides).** Python/Pillow in the Claude sandbox. IBM Plex Serif + Mono fetched from `https://github.com/IBM/plex/raw/master/packages/plex-serif/fonts/complete/ttf/{filename}.ttf`. Brand: `#0c0c0e` background, `#c4f04d` lime bar at top (action channel only), `#e8e6e1` text, "TORQUE BY RACEPROOF" overline, page dots with lime active indicator. Vertically center screenshots; crop tall screenshots (Seat Trends cropped to top 1290px) to preserve legibility. Output to `/mnt/user-data/outputs/`.

**LinkedIn hero:** 1200x627, single strong screenshot (identity fan worked well).

**Instagram cross-account amplification:** Collab invite (Edit > Tag People > Invite Collaborator on the published post) preferred; Native Repost or Story share as fallbacks. Never re-upload the carousel as a fresh post on the personal account.

**General asset rules:** never recreate brand assets from scratch when SVGs exist in the repo (`raceproof-site/public/images/`, `raceproof-docs/brand/Brand Mark/`). Google Fonts are unreliable in HTML-to-PDF workflows; use system fonts (Georgia, Helvetica, Courier New) for print output. Minimum font size 0.75rem everywhere.

## Link-in-bio workflow

`raceproof-site/public/links.html` is the link hub at `raceproof.app/links`. On every Torque publication: add the new article at the top of "Latest on Torque" with the "New" tag, demote the previous newest. Deploys via Cloudflare Pages on push to main (test-gated build).
