---
title: "Old Radio Voice Effect Summary"
tags:
  - audio-eq
  - voice-processing
  - vintage-effects
  - sound-editing
source: "https://voxbooster.com/blog/old-radio-voice-effect/"
author: "VoxBooster Team"
dateCreated: 2026-09-25
---

# Summary: Old Radio Voice Effect

*Source: [VoxBooster Team](https://voxbooster.com/blog/old-radio-voice-effect/) — published May 23, 2026*

## Core Thesis

The old radio voice effect is defined almost entirely by a tight bandpass filter (300–3400 Hz) that recreates the frequency limits of mid-20th-century AM broadcast and telephone circuits; light tube saturation completes the period-accurate character.

## Key Points

### Why 300–3400 Hz specifically

- Early broadcast circuits and telephone lines physically could not carry frequencies outside this "voice band."
- Below 300 Hz: chest resonance and proximity bass disappear — this is what makes the voice feel period-accurate rather than modern.
- Above 3400 Hz: crisp consonant "air" and mic-noise artifacts disappear, leaving speech slightly muffled but intelligible.
- 300 Hz is the article's recommended lower bound, not 200 Hz (still sounds modern) or 400 Hz (loses too much low-mid warmth).

### Filter settings

| Stage | Frequency | Slope | Removes |
|---|---|---|---|
| High-pass | 300 Hz | 12–24 dB/octave | Room rumble, chest resonance, HVAC hum, sub-bass |
| Low-pass | 3400 Hz | 12–24 dB/octave (similar to HPF) | Crisp consonants, room reflections, modern "air" (8–16 kHz) |

### Full EQ curve reference

| Frequency range | Treatment | Amount | Purpose |
|---|---|---|---|
| Below 200 Hz | High-pass | Steep roll-off | Remove room/chest bass |
| 200–300 Hz | Gentle cut | -6 to -9 dB | Tighten the low cut |
| 300–800 Hz | Slight boost | +1 to +2 dB | Warm low-mid body |
| 800–2000 Hz | Neutral | 0 dB | Core speech intelligibility |
| 2000–3000 Hz | Slight cut | -1 to -2 dB | Reduce modern "bite" |
| 3000–3400 Hz | Transition | -3 dB | Soft roll-off before cutoff |
| Above 3400 Hz | Low-pass | Steep roll-off | Remove modern clarity/air |

The 300–800 Hz boost is a starting point: lighter voices benefit from the boost, heavier voices may need it flat or slightly cut.

### Tube saturation (applied after filtering)

| Parameter | Value |
|---|---|
| Drive / input gain | Low — just touch the saturation threshold |
| Mix / wet | 20–40% |
| Harmonic mode | Even harmonics (2nd harmonic dominant) |
| Output gain | Match input level |

In Audacity, the Distortion effect ("Soft Clipping" / "Valve Overdrive") at drive 3–5/100 approximates this; a dedicated tape/tube plugin is more convincing in a full DAW.

### Related but distinct bandpass effects

| Parameter | Old Radio | Telephone | Megaphone |
|---|---|---|---|
| Bandpass | 300–3400 Hz | 300–3400 Hz | 500–4000 Hz |
| Saturation | Tube warmth (soft) | None/very slight | High (speaker distortion) |

Same bandpass as telephone, but radio adds tube warmth, noise, and compression for a fuller broadcast character.

## Relevance to Work

- [[202609251000 - Summary - Podcast EQ Settings Guide]] covers general speech EQ from a different source (mud/presence/de-essing) — useful contrast with this effect's deliberately narrow, destructive bandpass.
- [[202609251200 - Summary - Clear Voice Audio EQ]] and [[202609251200 - Summary - Character Voices Voice Acting]] are companion audio-processing references from the same capture batch.

## Related Reading

- [Telephone voice effect](https://voxbooster.com/blog/telephone-voice-effect)
- [Bitcrusher voice effect](https://voxbooster.com/blog/bitcrusher-voice-effect)
- freesound.org — referenced source for vinyl crackle/AM static samples
