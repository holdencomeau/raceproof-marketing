# Video (motion graphics) — channel recipe

**Status:** Format test launched 2026-07-02. First two videos live (Raceproof IG Reel + founder personal IG/LinkedIn). Established in response to unusually low engagement on static carousel posts.

**Why video:** Instagram Reels receive algorithmic distribution to non-followers; static carousels reach existing followers only. With a follower base near zero, carousel reach is structurally capped regardless of content quality. Reels are the reach test, not just a format refresh.

## Production recipe (proven 2026-07-02)

Frame-by-frame render in Python/Pillow, encoded with ffmpeg. No external tools, fully brand-controlled.

- **Spec:** 1080x1920 vertical, 30fps, target **under 20s** for completion rate (V4 shipped at 19.5s; V1 at 23s was flagged as slightly long).
- **Encode:** `ffmpeg -framerate 30 -i frames/%05d.png -c:v libx264 -pix_fmt yuv420p -crf 20 -movflags +faststart out.mp4`
- **Fonts:** IBM Plex Serif (display) + IBM Plex Mono (data), fetched from `github.com/google/fonts/raw/main/ofl/ibmplexserif/` and `.../ibmplexmono/` (the IBM/plex repo path in the carousel recipe has an unstable structure; the google/fonts mirror is reliable).
- **Brand:** `#0c0c0e` bg, `#e8e6e1` text, `#9c9b96` soft, `#6b6a65` muted. **Lime `#c4f04d` carries only measured data values and the URL** — not emphasis phrases, not question text. Lime top bar (14px) on brand-account videos; **no brand chrome on founder-voice videos until the end card** (chrome mid-confession reads as an ad).
- **End card (house style):** thesis line in Plex Serif SemiBold, "Raceproof measures it." soft, URL in lime mono, seven-threshold spectrum band (`#F9E16C #F4BB57 #EF8843 #E95335 #E22840 #C72370 #A7258D`) fading in along the bottom edge.
- **Motion language:** the data draws itself (axis strokes in, dot travels and lands, values count up). No stock footage, no gimmicks; the animation carries the same factual voice as the prose. Text reveals use 16px rise + fade (mirrors the Torque `.reveal` style). Cubic in-out easing.
- **Audio:** renderer produces silent video by design. Add trending/ambient audio in the Instagram composer at post time (also helps reach). LinkedIn upload stays silent-safe (assume sound-off viewing; the video must work mute).

## Composition rules (learned the hard way)

1. **Reels safe zones:** keep key content roughly y 250–1550. First render placed the axis at y≈1690, inside the caption/UI zone. Move up.
2. **Never crossfade two lines at the same y-position.** Overlapping fade-out/fade-in double-exposes. Stagger: old line fully out before new line enters.
3. **One element fades fully before its replacement concept arrives** (confusion lines must reach alpha 0 before the axis draws through their zone).
4. Timing as named frame constants (`B1…B7`) at the top of the render script; pacing iteration is then edits to constants, not rework. Pacing judgment is Holden's (perceptual calibration; can't be pre-verified in stills).
5. Review via keyframe strips before encoding; extract 5–7 frames across all beats into one image.

## Script architecture (the two proven arcs)

**V1 "The Unit Swap" (brand voice):** known question → instant watts answer → same question in the unit nobody can answer → the three conventional answers, "none of them measured" → axis, measured coordinate lands → thesis + URL.

**V4 "The Confession" (founder voice):** first-person credibility line → instant FTP answer → "it has a second number" → measured coordinate with date label → **the dot moves** (Jun 10 19:09 → Jul 1 19:01, date label swaps) → thesis + URL. The moving dot demos the product's actual job: tracking movement.

Every number shown must be screenshot-verified article data (editorial standard applies to video). Invented illustrative data (e.g. a hypothetical second rider) requires explicit hypothetical framing and was rejected for the first test.

## Two-account distribution pattern

- **Brand account:** brand-voice video (V1 style), professional register.
- **Founder personal account:** confession-voice video (V4 style) with **collab invite to @raceproof** (both grids, founder's face on it). First-person outperforms brand voice on Reels by convention.
- **LinkedIn (founder):** native video upload, **link in first comment only** (external links in body suppress reach).
- **Posting order:** LinkedIn first (weekday late-morning window), founder IG collab second, brand IG a few hours later so the two Reels don't compete in one feed session.

## Title/hook methodology (established during the retitle)

The article title and the video hook are the same asset. What worked: riff on the sport's common spoken language and swap the unit ("What's your FTP?" is answered in watts; ask it in minutes). Rules extracted:
- A research publication states or directly poses a resolvable question; it never teases ("The Number You Can't Name" withheld, and was retired for it).
- A question title is defensible only if the article answers it.
- Avoid ambiguous words: "long" reads as distance as easily as time; "minutes" is unambiguous.
- The title should hand the social channels their hook verbatim.
