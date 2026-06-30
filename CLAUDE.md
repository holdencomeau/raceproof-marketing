# raceproof-marketing — Session Briefing

## What this is

Marketing assets, strategy, and campaign content for Raceproof. This repo holds copy, social media content, outreach materials, competitive positioning, and any marketing deliverables.

Raceproof is a cycling performance analytics platform built on a proprietary physiological framework called the Power Threshold Array (PTA). The platform's core value proposition is a unified measurement system across seven energy systems — filling an integration gap that existing tools (TrainingPeaks, Strava, intervals.icu) don't address. The slogan is **"There's more to you."**

## Product context lives in raceproof-docs

This repo does not contain product documentation, algorithm descriptions, or brand specifications. All of that lives in the `raceproof-docs` repo. **Read raceproof-docs before writing anything.**

Clone it adjacent to this repo:
```
C:\Users\HoldenComeau\CLAUDE\Docs\RaceProof\
├── raceproof-marketing/    ← you are here
├── raceproof-docs/         ← product knowledge base
├── raceproof-api/          ← backend
├── raceproof-site/         ← frontend
└── raceproof-torque/       ← data journalism publication
```

### Reference files by task

**Before any marketing work**, read `raceproof-docs/CANONICAL_STATE.md` — the single source of truth for what has shipped, what's in progress, and what's planned.

| Task | Read first |
|---|---|
| Any copy or messaging | `brand/BRAND_GUIDE.md`, `brand/DESIGN_PHILOSOPHY.md` |
| Social media posts | `brand/SOCIAL_MEDIA_VOICE_GUIDE.md` |
| Describing PTA / thresholds / seats | `pta/PTA_MASTER_REFERENCE.md` |
| Describing Loom | `loom/LOOM_VARIABLE_LOCKDOWN.md`, `knowledge/product/LOOM_REDESIGN.md` |
| BD conversations, partner decks | `knowledge/commercial/ALGORITHM_REFERENCE.md` (BD-safe, no IP) |
| Competitive positioning | `knowledge/commercial/COMPETITIVE_MODEL_RESEARCH.md` |
| Wordmark / logo usage | `brand/BRAND_MARK_GUIDE.md`, `brand/Brand Mark/` (exported assets) |
| Visual design (posters, ads, social graphics) | `brand/VISUAL_DESIGN_PROCESS.md` |
| Trademark claims | `legal/TRADEMARK_FIRST_USE.md` |
| What we can't reveal | `legal/TRADE_SECRET_INVENTORY.md` |

### Key product concepts for marketing

- **PTA (Power Threshold Array):** Seven physiological thresholds (PT-N, PT-S, PT-G, PT-X, PT-O, PT-V, PT-T), each a position in power × offset space. "Threshold Offset" not "onset."
- **Seat:** A position in power × offset space. The atomic analytical unit. Each seat corresponds to a distinct energy system.
- **Loom:** The career visualization (flagship trademark). A visual record of an athlete's entire training history.
- **Torque:** The data journalism publication at `torque.raceproof.app`.
- **Expression:** A self-referenced fitness metric. `(offset / peakOffset) × (power / peakPower)`.
- **Trust Score:** Data governance and certification mechanism. Trust is personalization, not judgment.
- **Offset:** The duration at which a threshold fires. The novel measurement PTA introduces. Power provides trend context; offset is the new thing.

## Active trademarks

Raceproof, Loom, Torque, PTA, Seat, Expression, Trust Score, Proof Network, MasterActivity.

## Brand rules

### Color channels — these do not mix

| Channel | Color | Use |
|---|---|---|
| Action | Lime `#c4f04d` | CTAs, interactive elements, buttons |
| Physiology | Per-seat hues | Encoding physiological identity (never decorative) |
| Power context | Sage green `#6ea87a` | Power values and trends |
| Narrative | Off-white | Body text, prose, explanations |

### Wordmark

The RACEPROOF wordmark is always an image file (SVG/PNG from `brand/Brand Mark/`), never styled text. Two overlapping O rings replace the text O's. The LOOM wordmark follows the same pattern.

### Typography

DM Sans is the primary typeface. Minimum font size: 0.75rem (12px) for all text, no exceptions.

### Things that are always wrong

- Mixed-case "RaceProof" (it's RACEPROOF in the wordmark, "Raceproof" in prose)
- Lime used for anything other than action/CTAs
- Seat hues used decoratively
- Referring to PTA as "PT-A"
- The term "Effort Signature" or "Fingerprint" (deprecated, never use)
- Referring to Raceproof as anti-cheat, validation, or verification
- Any claim that cycling "only had one metric" before PTA (it had many; PTA unifies them)

## Editorial standards

### Factual precision is non-negotiable

All factual claims must be validated before publication. The founder's opinions are not publishable fact. If a claim can't be verified, it doesn't ship.

Competitive claims about other products (TrainingPeaks, Strava, intervals.icu, WKO, Xert) must be verified against primary sources — company documentation, published research, official announcements. Forum complaints and social media sentiment are not sufficient.

The standard: **could this sentence survive a public challenge from the company named in it?**

### Voice

- Confident, not aggressive. Raceproof doesn't need to tear others down.
- Factual, not literary. Let the data carry the argument.
- Specific numbers over vague claims. "Seven thresholds" not "multiple thresholds."
- No performative warmth or hype language. No "revolutionary" or "game-changing."
- The Torque publication voice guide (`brand/SOCIAL_MEDIA_VOICE_GUIDE.md`) applies to all external-facing content.

### IP boundaries

Marketing can describe **what** the algorithms do and **why** they matter. Marketing never reveals **how** — no weights, no calibration constants, no scoring formulas, no population baselines. The BD-safe reference at `knowledge/commercial/ALGORITHM_REFERENCE.md` defines the public/private boundary. Stay inside it.

## What NOT to do

- Do not write marketing copy without reading raceproof-docs first. The product changes constantly. Stale claims are wrong claims.
- Do not commit API keys, athlete IDs, or secrets.
- Do not use anti-cheat / validation / verification language anywhere.
- Do not reveal IP-sensitive numbers in any content.
- Do not claim features that haven't shipped. Check CANONICAL_STATE.md.
- Do not use "Effort Signature," "Fingerprint," or "PT-A."
- Do not describe trust scoring as judgment. It's personalization.

## Workflow

Strategy and scoping happen in the main Chat session (the same one that manages all Raceproof work). Execution happens via Claude Code sessions initialized in this repo.

Code sessions should:
1. Read `CANONICAL_STATE.md` from `raceproof-docs` at session start
2. Read the relevant brand/product reference files for the task
3. Execute the task as specified
4. Write a completion note if the work is substantial

No separate backlog. Work is tracked on `raceproof-docs/TASK_BOARD.md` alongside all other Raceproof work.
