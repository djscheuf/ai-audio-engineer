---
title: "Podcast EQ Settings: The Complete Guide for Clear Voice Audio Summary"
tags:
  - podcast-production
  - audio-eq
  - voice-processing
  - Reaper
  - GarageBand
source: "https://podigy.co/blog/podcasters-eq"
author: "Riley Byrne"
dateCreated: 2026-09-25
---

# Summary: Podcast EQ Settings: The Complete Guide for Clear Voice Audio

*Source: [Riley Byrne on Podigy](https://podigy.co/blog/podcasters-eq) — published January 25, 2024; updated March 17, 2026*

## Core Thesis

EQ is the highest-leverage post-production tool for podcast vocals. The professional approach is to remove problems first—rumble, mud, and room resonance—before adding subtle presence or air, which produces clear, trustworthy-sounding voices without amplifying background noise.

## Key Points

### EQ philosophy: cut first, boost rarely

Cutting unwanted frequencies gives the same perceived clarity as boosting the opposite range, but it leaves noise and room artifacts untouched. The main exception is a gentle high-shelf boost above 8 kHz for air, where typical vocal recordings have little noise energy.

### Essential frequency ranges for podcast voices

| Range | Name | What it affects | Typical action |
|---|---|---|---|
| Below 80 Hz | Rumble zone | Desk thumps, HVAC, plosives | High-pass filter on every track |
| 80–120 Hz | Warmth/body | Vocal weight and richness | Cut only if boomy; never remove entirely |
| 150–300 Hz | Proximity/mud zone | Condenser proximity effect, room modes | Bell cut 2–4 dB around 200–280 Hz |
| 300–800 Hz | Room reflections | Boxy, "recorded in a room" sound | Narrow bell cut at specific resonances |
| 1–2 kHz | Nasal honk zone | Pinched, whiny quality | Notch cut at the offending frequency |
| 2–5 kHz | Clarity/presence | Word intelligibility | Small 1–2 dB boost if needed |
| 5–8 kHz | Sibilance zone | Sharp S/T/SH sounds | Use a de-esser, not EQ |
| 8–12 kHz | Air/brightness | Openness and polish | Gentle 1–2 dB high-shelf boost if dull |
| 15 kHz+ | Harsh upper range | Harshness in compressed audio | Low-pass roll-off around 15–16 kHz |

### Scenario-specific starting points

| Format | Typical setup | Key EQ moves |
|---|---|---|
| **Interview** | Condenser mics in home offices | HPF @ 80 Hz; -3 dB bell @ 240 Hz Q≈1.2; -2 dB @ 350 Hz; +1.5 dB @ 2.5 kHz; +1.5 dB high shelf @ 9 kHz; low-pass @ 15 kHz |
| **Solo narration** | Dynamic mic in treated space | HPF @ 100 Hz (18 dB/oct); -2 dB @ 220 Hz; -1.5 dB @ 500 Hz; +1 dB @ 3 kHz; +1 dB high shelf @ 10 kHz |
| **Panel/roundtable** | Mixed mics, remote guests | HPF @ 80 Hz; -2 to -4 dB @ 200 Hz; -1.5 dB @ 400 Hz; +1 dB @ 2 kHz; low-pass @ 15 kHz for consistency |

### Common voice problems and EQ fixes

| Problem | Symptom | Fix |
|---|---|---|
| **Boomy/muddy** | Thick, boxy, "speaking from a box" | Bell cut 200–280 Hz, Q 1.0–1.5, -3 to -5 dB |
| **Thin/weak** | Hollow, telephone-like | Low-shelf boost 100–150 Hz +1–2 dB; check HPF is not above 100 Hz |
| **Nasal/honky** | Pinched, whiny | Notch cut 800 Hz–2 kHz, Q 6–8, -4 to -6 dB |
| **Sibilance** | Sharp S/T/SH | Use a de-esser; static EQ cuts make everything dull |
| **Room resonance** | Hollow drone under the voice | Narrow bell cuts 300 Hz–1 kHz, Q 4–6, -3 to -6 dB |
| **Proximity buildup** | Unnaturally deep and boomy | Bell cut 150–280 Hz, Q 1.0–1.2, -2 to -4 dB |

### Common mistakes to avoid

- **Boosting before cutting** — identify and remove problem frequencies first.
- **High-passing above 100 Hz** — this strips vocal body and sounds unnatural.
- **Using the same preset on every voice** — mic distance, voice type, and room change the target curve.
- **Over-processing** — more than five or six active bands usually means you are fixing recording or room problems that EQ cannot solve.
- **EQing on bass-boosted consumer headphones** — use flat reference headphones (e.g., Sony MDR-7506, Audio-Technica ATH-M40x) for critical decisions.

## Technical Details

### Effects-chain placement

Place EQ after noise reduction/denoising and before compression, so the compressor responds to the tonal shape you actually want:

`Noise reduction → EQ → Compression → De-esser → Limiter`

### ReaEQ starting setup (interview format)

```text
Band 1: High Pass, 80 Hz, 0.7 oct
Band 2: Bell, 240 Hz, -3 dB, 0.5 oct
Band 3: Bell, 2500 Hz, +1.5 dB, 0.6 oct
Band 4: High Shelf, 9000 Hz, +1.5 dB
```

In Reaper’s ReaEQ, the **Bandwidth** control is in octaves, not Q: ~0.5 oct ≈ Q 1.4 and ~0.2 oct ≈ Q 3.5. GarageBand’s Channel EQ is simpler but does not expose precise Q values, so surgical notch work is easier in Logic Pro or Reaper.

## Relevance to Work

- [[202609251200 - Summary - Character Voices Voice Acting]] overlaps on vocal performance and recording technique; its related reading also links to a podcast-mic setup guide.
- [[202609251000 - Summary - Podcast EQ Settings Guide]] offers an alternate framing of podcast EQ starting points and common fixes from PodRewind.

## Related Reading

- [De-essing for Podcasts](https://podigy.co/blog/de-essing-for-podcasts)
- [Compression for Podcasts](https://podigy.co/blog/compression-for-podcast)
- [Top Podcast Recording and Editing Software](https://podigy.co/blog/top-podcast-recording-and-editing-software)
