---
title: "Podcast EQ Settings Guide Summary"
tags:
  - podcast-production
  - audio-eq
  - voice-processing
  - sound-editing
source: "https://podrewind.com/blog/podcast-eq-settings-guide"
author: "PodRewind Team"
dateCreated: 2026-09-25
---

# Summary: Podcast EQ Settings Guide

*Source: [PodRewind Team](https://podrewind.com/blog/podcast-eq-settings-guide) — published October 30, 2025*

## Core Thesis

Podcast EQ is not about changing how a voice sounds but about removing problems and enhancing clarity so listeners hear natural, professional speech; the best results come from small (2–4 dB) subtractive moves first, followed by subtle presence or air adjustments.

## Key Points

### EQ principles

- **Subtractive first.** Cut problem frequencies before boosting; cutting is cleaner and less likely to add noise or artifacts.
- **Small moves.** Most adjustments should be 2–4 dB; dramatic curves usually mean the recording or room has deeper problems.
- **Invisible processing.** The goal is a natural-sounding voice, not an obviously EQ'd one; listeners should notice clarity, not effects.
- **A/B every change.** Bypass the EQ and compare at matched loudness; if the original sounds better, reduce the adjustment.
- **Document settings.** Save speaker-specific EQ notes (name, mic, settings, special considerations) to speed up future episodes.

### Essential frequency ranges for speech

| Frequency | Element | Character | Typical action |
|---|---|---|---|
| 80–125 Hz | Chest resonance | Weight, power | Preserve unless boomy |
| 125–250 Hz | Fundamental tone | Warmth, body | Preserve; boost slightly if thin |
| 250–500 Hz | Lower harmonics | Fullness or muddiness | Cut 2–4 dB if boxy |
| 500 Hz–1 kHz | Mid presence | Honky or nasal if excessive | Narrow cut if nasal |
| 1–3 kHz | Upper harmonics | Clarity, intelligibility | Preserve or boost gently |
| 3–6 kHz | Presence | Definition, cut-through | Small boost for clarity |
| 6–10 kHz | Sibilance | "S" sounds, air | Use a de-esser, not static EQ |
| 10 kHz+ | Air | Sparkle, breathiness | High-shelf cut if harsh |

### Core EQ moves

| Move | Frequency / range | Action | Purpose |
|---|---|---|---|
| High-pass filter | 80–100 Hz (12–24 dB/oct) | Roll off | Remove rumble, HVAC, handling noise |
| Mud reduction | 200–400 Hz | Cut 2–4 dB, Q ≈ 1–2 | Fix boxy, boomy quality |
| Presence boost | 2–5 kHz | Boost 1–3 dB, wide Q | Improve intelligibility |
| High-frequency roll-off | 10–12 kHz | Cut 2–4 dB or gentle low-pass | Reduce harshness and fatigue |

### Common voice problems and fixes

| Problem | Symptom | Fix |
|---|---|---|
| Muddy/boomy | Thick, boxy, unclear | HPF at 100 Hz; cut 2–4 dB at 200–300 Hz |
| Thin/nasal | Lacks body, tinny, honky | Lower HPF to 60–80 Hz; boost 1–2 dB at 200–250 Hz; cut 2–3 dB at 800 Hz–1 kHz |
| Harsh/fatiguing | Sibilance prominent, tiring | Cut 2–4 dB at 4–6 kHz; low-pass above 10–12 kHz; use a de-esser |
| Muffled | Sounds behind a curtain | Boost 2–3 dB at 2–4 kHz; high-shelf boost 1–2 dB above 6 kHz |
| Plosives | "P" and "B" thuds | High-pass at 100–120 Hz helps partially; prefer pop filter and manual/de-plosive repair |

### Starting settings by voice type

| Voice type | High-pass | Body / mud | Presence / clarity | Air / harshness |
|---|---|---|---|---|
| Deep male | 80 Hz | Cut 3 dB at 250 Hz | Boost 2 dB at 3 kHz | — |
| Higher male | 90 Hz | Boost 1–2 dB at 200 Hz if thin | Boost 2 dB at 3–4 kHz | — |
| Average female | 100 Hz | Cut 2 dB at 350 Hz if boxy | Boost 2 dB at 4 kHz | Cut 2 dB at 5–6 kHz if harsh |
| Higher female | 110 Hz | Boost 1 dB at 250 Hz | Boost 1–2 dB at 4–5 kHz | High-shelf cut 2 dB above 8 kHz |

These are starting points; every voice, mic, and room combination is different.

## Technical Details

### Signal-chain order

Place EQ after noise reduction and before compression so the compressor responds to the tone you actually want:

`Noise reduction → EQ → Compression → De-essing → Limiting`

### Sweeping to find a problem frequency

To locate a boxy or resonant build-up:

1. Create a narrow boost (+6 dB, high Q) in the suspect range.
2. Sweep slowly until the problem sounds most pronounced.
3. Switch the boost to a 2–4 dB cut at that exact frequency.

## Relevance to Work

- [[202609251200 - Summary - Clear Voice Audio EQ]] covers a similar parametric-EQ workflow from a different source and makes a good companion reference.
- [[202609251200 - Summary - Character Voices Voice Acting]] overlaps on vocal performance, recording technique, and microphone positioning.
- [[The Voice is an Instrument]] treats the voice as a musical instrument and covers warm-ups and range awareness.

## Related Reading

- [Podcast Editing Workflow](https://podrewind.com/blog/podcast-editing-workflow)
- [Why Podcast Transcripts Matter](https://podrewind.com/blog/why-podcast-transcripts-matter)
