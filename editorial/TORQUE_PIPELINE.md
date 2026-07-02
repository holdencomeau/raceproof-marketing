# Torque — Editorial Pipeline State

**Status:** CANONICAL for editorial pipeline state. Voice and stance bylaws live in `raceproof-torque/CLAUDE.md` and govern all prose.
**Last reviewed:** 2026-07-02

---

## Published inventory (2026-07-02)

Source of truth for what is published is the `build_index.py`-generated `index.html` in `raceproof-torque/`, not this list. This list exists for editorial planning context.

| Article file | Role | Notes |
|---|---|---|
| `the_number_you_cant_name.html` | **Featured** (`torque:order=0`), published 2026-07-02 | The offset on-ramp. Teaches offset through PT-T (the familiar FTP seat) first, then PT-G. Six sections. Four Activity Detail figures, screenshot-verified: PT-T Jun 10 / Jul 1 (Wednesday Worlds), PT-G Jun 26 (Happy Hour) / Jun 18 (Thursday Thumper). |
| `your_ftp_is_a_seat.html` | FTP-to-PTA bridge (`torque:order=2`) | Carries the open independence overclaim (below). |
| `what_power_alone_cant_tell_you.html` | Data-journalism proof piece | 222-session finding; referenced in Discord repurpose announcement. |
| `how_to_read_a_seat.html` | Reference piece | Research basis other articles point to. Audit `#offset` section for the independence claim. |
| `model_depth.html`, `loom.html`, `the_racing_effect.html`, `the_shape_of_the_heat.html` | Back catalog | |

`threshold_matrix_standalone.html` exists in `articles/` but is not counted in the 8 live posts per CANONICAL_STATE; verify its index status before touching order values.

## Publishing workflow

1. Write article HTML into `raceproof-torque/articles/` on the established template (Source Serif 4 / IBM Plex Sans / IBM Plex Mono, dark-adaptive palette, `.fig` / `.callout` / `.link-card` components, `torque:*` meta tags).
2. Set `torque:order` (integers only; `build_index.py` casts with `int()`). Featured article is order 0; only the featured article gets the "New" badge.
3. Run `python build_index.py`. Never hand-edit `index.html`.
4. Update `raceproof-site/public/links.html`: new article at top of "Latest on Torque," demote the previous one. Instagram bio points at `raceproof.app/links`.
5. All figures screenshot-verified against the live app. Figure crop standard from the 2026-07-02 publication: uniform frame, scarf plus the full left readout column, cut just below the panel border, so data values stay legible on mobile.
6. Social distribution pass is a separate step (see `channels/SOCIAL.md`).

---

## Open item 1 — Independence overclaim correction

**The problem.** `your_ftp_is_a_seat.html` contains a live `.ann` block: "The deeper treatment of why power and duration move independently, with the published research behind it, lives in How to Read a Seat." Verified in-file 2026-07-02. Founder-corpus per-ride data shows offset changes and power changes correlate at r = 0.62. "Move independently" is an overclaim the data contradicts.

**The correction.** State honestly that offset and power carry different information and move on different timescales. Do not claim mathematical independence or orthogonality. The two-coordinate claim survives the correction intact: a correlated second coordinate still carries information the first does not.

**Scope.** Fix the sentence in `your_ftp_is_a_seat.html`; audit `how_to_read_a_seat.html#offset` (the pointer target) for the same claim; re-run `build_index.py` is not needed for in-place prose edits, but the correction should be noted in a session summary.

## Open item 2 — The trajectory / durability piece (raw material)

The teaching arc of the stalled "Every Threshold Has a Duration" draft shipped on 2026-07-02 as "The Number You Can't Name," built on single-ride figures. The deeper conceptual piece diagnosed on 2026-06-29/30 has not been written. Its material:

**Argumentative foil.** Every threshold protocol in cycling prescribes a duration (20 min, 60 min, 8 min) and treats it as a fixed input to the test. Those durations are protocol design decisions, not physiological measurements of an individual. PTA measures duration as a physiological output specific to the athlete, per threshold, and tracks how it moves with training. Note the trap two prior drafts fell into: the duration has always been *measured* (every protocol specifies one); what has never been done is explain what that duration means physiologically for a specific athlete or track it as an output.

**Evidence spine.** PT-T offset trajectory across 37 rides (2026-01-30 to 2026-04-01): offset moved from roughly 1170s to 1202s while power held near 341W. The raw per-ride data shows a **staircase**: three large step-changes with long plateaus, not linear drift. A linear-trend summary obscured this; raw per-ride interrogation is mandatory before accepting any summarized narrative.

**Literature positioning.** The sports science "durability" literature (Maunder, Van Erp, Clark) recognizes durability as an independent parameter uncorrelated with VO2max or FTP, and finds W' (the power-duration curvature parameter) significantly less reliable than critical power in repeat testing. Frame PTA's offset as the per-threshold coordinate that field has been converging toward. State what PTA adds, never what competitors lack.

**Honesty constraint.** The piece must be consistent with the Open item 1 correction: no independence claim.

**Data provenance.** Trajectory data came from a Code handoff (`TORQUE-OFFSET-DATA-001.md`) against `/pta/v3/evolution/` with an explicit IP wall: no internal constants, tau thresholds, search ranges, or calibration parameters. Any refresh of this data must carry the same wall.

## Editorial failure modes (do not repeat)

Recorded from the June 2026 drafting arc so future sessions do not rediscover them:

1. **UI tutorial pretending to be an argument.** Two single-ride screenshots cannot carry a conceptual thesis. Match the evidence to the size of the claim.
2. **Literary devices and structural tropes.** The Torque voice is factual and non-emotional. No reaching for effect. Let the facts carry the argument.
3. **Restating the founder's thinking back at him.** Claude's role is additive: original research, new information, real analysis.
4. **Trusting a summary over the raw data.** The staircase was hidden by a linear-trend summary. Interrogate per-ride data first.
5. **Single-ride deltas as evidence.** +0.1s of offset movement is noise-scale. Trajectory across many rides is the unit of evidence.
6. **"The ride is not the seat"** is the anchor distinction (what a ride produces vs where the seat moves) and it is now published in "The Number You Can't Name." New pieces build on it rather than re-teach it.
