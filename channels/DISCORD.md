# Discord — Community Channel State (Marketing View)

**Status:** POINTER DOC. The Discord system's canonical docs are `raceproof-discord/SERVER_SPEC.json`, `raceproof-discord/docs/SERVER_DESIGN.md`, and `raceproof-docs/planning/DISCORD_AGENT_PROJECT.md`. This file holds only what marketing sessions need.
**Last reviewed:** 2026-07-02

---

## State

- Server live, renamed Raceproof (repurposed from Half Wheel Coaching 2026-06-11; ~31 human members at migration, former coaching community). Coaching-era archive permanently deleted 2026-06-12.
- Repurpose announcement published from `raceproof-discord/templates/welcome-announcement.md`: first person, references the 222-session finding from "What Power Alone Can't Tell You," beta invitation stated once. Voice rule from that draft's correction: attribute the coaching past to the server's history, never to the members' identity.
- Beta funnel integration: Discord beta invitations route through the standard pipeline (raceproof.app apply, then Postgres and Klaviyo sync, then role sync grants the Beta role), so accepting members also land on the Klaviyo lists.
- `#torque-article-discussion` exists for article rollouts; each Torque distribution pass includes a Discord announcement with one discussion-seeding question.

## Capabilities and their gates

| Capability | State | Gate |
|---|---|---|
| Digest (Anthropic-drafted from public-channel activity + new Torque posts) | Built, disabled | Founder-triggered only (`POST /trigger/digest`), Admin reaction approval in `#bot-ops`, `ENABLE_DIGEST=false` until `ANTHROPIC_API_KEY` set on Railway. Member-facing posts are never scheduled. |
| Q&A agent (DISCORD-QA-001) | Ready for Code | Caged to published-content-only knowledge base. Hard refusals on architecture, sampling methodology, data-infrastructure internals. QA_VOICE persona approved 2026-06-12. `ENABLE_QA` ships false; red-team eval suite is the launch gate. |
| ZwiftPower data layer (Phase 4) | Future | Would upgrade the Q&A agent to tool-using via `zwiftpower-query` / `zwiftpower-etl`. |

## Brand notes

Lime `#c4f04d` is the single action-channel accent inside Discord (Beta role only). The three-channel law holds for all other role colors.
