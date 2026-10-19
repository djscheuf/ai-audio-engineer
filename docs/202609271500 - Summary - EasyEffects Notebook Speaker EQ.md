---
title: "Enhancing Your Internal Notebook Speakers Without Using an Equalizer Summary"
tags:
  - easyeffects
  - audio-dsp
  - pipewire
  - linux
  - speaker-eq
source: "https://wwmm.github.io/easyeffects/guides/guide_1.html"
author: "Markus Schmidt"
dateCreated: 2026-09-27
---

# Summary: Enhancing Your Internal Notebook Speakers Without Using an Equalizer

*Source: [Markus Schmidt, EasyEffects Manual](https://wwmm.github.io/easyeffects/guides/guide_1.html) — written Nov 2019 for PulseEffects, updated for EasyEffects/PipeWire*

## Core Thesis

Tinny, bass-less notebook speakers are best improved with a fixed chain of dynamic processors (Filter → Bass Enhancer → Multiband Compressor → Stereo Tools → Limiter), not a static Equalizer — because an EQ can only redistribute energy the tiny drivers already can't produce, while these processors add missing harmonics and dynamically reshape the signal.

## Why Not an Equalizer

- Additive EQ boosts frequencies the speaker/amp can't reproduce louder — leads to distortion when volume is raised to compensate.
- Subtractive EQ removes energy instead, but notebook amps aren't loud enough to begin with, so the result is quiet and still thin.
- EQ is static; the real problems (missing bass, harsh highs, narrow dynamic range) need dynamic, frequency-dependent processing instead.

## Signal Chain & Settings

Build in this order (top of list = first processed); Limiter goes last in the chain but is configured first since nothing should exceed 0 dB at the DAC.

| Order | Plugin | Key Settings | Purpose |
|---|---|---|---|
| 1 | **Filter** | Type: 36 dB High Pass; Frequency: start at 50 Hz, raise by 10 Hz until you hear a change (~130–160 Hz), then subtract ~10% (15 Hz) | Remove frequencies the speaker can't reproduce at all, wasting energy/headroom |
| 2 | **Bass Enhancer** | Floor: 10 Hz; Harmonics: 10; Scope: start at 200 Hz; Amount: raise until bass dominates, then back off (example: +24 dB) | Adds 2nd/3rd-order harmonics above the missing fundamental so bass becomes audible on small drivers |
| 3 | **Multiband Compressor** | Input gain: -6 dB starting point; Bands 2/3/4 enabled; Modern Operating Mode; Sidechain Boost off; Compression Mode: Downward on all bands | Tames dynamic range and reshapes overall frequency balance — the "Makeup" per band is effectively your EQ replacement |
| 4 | **Stereo Tools** | Output tab → Stereo Base: 0.25 (try 0–0.5) | Widens the stereo image without collapsing bass (negative values push toward mono) |
| 5 | **Limiter** | PreAmp: 0 dB; Lookahead: 4 ms; Attack: 2 ms; Release: 8 ms; Threshold: 0 dB; Stereo Link: 100%; Oversampling: Half x4; External Sidechain & Auto Leveling: off | Fire-and-forget safety net preventing clipping at the sound card DAC once the earlier stages push levels up |

### Multiband Compressor band defaults

Split frequencies: Band 2 @ 250 Hz, Band 3 @ 1250 Hz, Band 4 @ 5000 Hz.

| Band | Attack | Release | Threshold | Ratio | Knee | Makeup |
|---|---|---|---|---|---|---|
| 1 | 150 ms | 300 ms | -16 dB | 5 | -12 dB | 4 dB |
| 2 | 150 ms | 200 ms | -24 dB | 3 | -9 dB | 4 dB |
| 3 | 100 ms | 150 ms | -24 dB | 3 | -9 dB | 4 dB |
| 4 | 80 ms | 120 ms | -24 dB | 4 | -9 dB | 4 dB |

Per-band **Makeup** is the real tone-shaping control here (raise/lower a band to make it louder/quieter); the author's own machine ended up at 4/3/6/6 dB across bands 1–4. **Input Level** (default -6 dB, author used -3 dB) pushes all bands up together for perceived loudness at the cost of dynamic range.

## Frequency Range Reference

| Range | Approx. Hz | Character |
|---|---|---|
| Sub | 10–40 | Barely audible vibration |
| Low/Bass | 60–200 | Fundament, kick/bass drums — missing entirely on notebooks |
| Low-Mid | 250–750 | "Punch," snare/guitar body |
| High-Mid | 1k–4k | Most sensitive range; voice, main signal information |
| Highs | 5k+ | Air, breath, sizzle |

## Relevance to Work

- [[202609251500 - Summary - Old Radio Voice Effect]] and [[202609251200 - Summary - Clear Voice Audio EQ]] cover the same 5-band frequency vocabulary (rumble/bass, mud, presence, air) from a vocal-EQ angle — useful contrast between subtractive voice EQ and this dynamic, additive speaker-correction chain.

## Related Reading

- Test signal used by the author: [G€LD by Seeed](https://www.youtube.com/watch?v=OxAP6ieuDgI)
- [EasyEffects Plugins Database](https://wwmm.github.io/easyeffects/database/plugins_properties.html) — full parameter reference for Filter, Bass Enhancer, Multiband Compressor, Stereo Tools, Limiter
