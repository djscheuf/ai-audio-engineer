# AI as My Audio Engineer

Companion repository for the blog post **AI as My Audio Engineer**.

> AI puts the average expertise of a wide variety of knowledge domains at your fingertips. This repo shows what that looks like in practice: turning AI into an audio engineer with a few prompts, some article summaries, and a knowledge skill built from the Easy Effects documentation — all stitched together into working PipeWire audio presets.

## The Story

The blog post walks through a real experiment: I wanted to get the most out of a podcasting mic after an office move, without becoming an audio engineer. The workflow was:

1. **Research** — use AI to summarize articles on podcast EQ and voice effects.
2. **Capture tool knowledge** — use the `create-knowledge-skill` pattern to turn the Easy Effects docs into a focused, reusable skill.
3. **Generate config** — ask the AI, armed with the skill, to produce Easy Effects JSON presets for a clean podcast voice and an old-timey AM radio voice.
4. **Iterate and tune** — load the presets, listen, and adjust.

The result was good enough that people on calls started asking, "Have you ever been in radio?"

## What's in This Repo

```text
ai-audio-engineer/
├── configs/                          # Ready-to-load Easy Effects presets
│   ├── Podcaster.json
│   └── OldTimeyRadio_Corrected.json
├── docs/                             # Article summaries that informed the presets
│   ├── 202609251000 - Summary - Podcast EQ Settings Guide.md
│   ├── 202609251200 - Summary - Clear Voice Audio EQ.md
│   ├── 202609251500 - Summary - Old Radio Voice Effect.md
│   └── 202609271500 - Summary - EasyEffects Notebook Speaker EQ.md
├── .agents/skills/                   # Agent skills used in the workflow
│   ├── article-summary/SKILL.md
│   ├── create-knowledge-skill/SKILL.md
│   └── easyeffects-plugins/          # Knowledge skill distilled from Easy Effects docs
│       ├── SKILL.md
│       ├── local-server.md
│       ├── dynamics.md
│       ├── tone-eq.md
│       ├── noise-reduction.md
│       ├── spatial-time.md
│       ├── pitch.md
│       └── utility.md
└── LICENSE
```

## Skills

### `article-summary`

[`.agents/skills/article-summary/SKILL.md`](.agents/skills/article-summary/SKILL.md)

A reusable prompt for summarizing web articles into a consistent, knowledge-base-friendly format. Used here to turn podcast-EQ and voice-effect articles into the concise reference notes in `docs/`.

### `create-knowledge-skill`

[`.agents/skills/create-knowledge-skill/SKILL.md`](.agents/skills/create-knowledge-skill/SKILL.md)

The pattern for turning an external documentation site into a progressive-disclosure agent skill. In the blog post, this is the key step that lets AI ratchet its own ability in a subdomain — in this case, Easy Effects.

### `easyeffects-plugins`

[`.agents/skills/easyeffects-plugins/SKILL.md`](.agents/skills/easyeffects-plugins/SKILL.md)

A domain-specific knowledge skill distilled from the [Easy Effects documentation](https://wwmm.github.io/easyeffects/). It covers the available plugins, their parameters, and how to script them via the local server socket.

Use it when you want AI to help you build or modify an Easy Effects effects chain without re-reading the full docs each time.

## Configs

All presets are `input` chains for Easy Effects on PipeWire. Load them via the GUI, or use the local socket:

```sh
# Load the podcaster preset into the input/microphone pipeline
echo "load_preset:input:Podcaster" | socat - UNIX-CONNECT:$XDG_RUNTIME_DIR/EasyEffectsServer
```

### `configs/Podcaster.json`

[`configs/Podcaster.json`](configs/Podcaster.json)

A clean, modern podcast-voice chain:

| Stage | Plugin | Purpose |
|-------|--------|---------|
| 1 | Noise Reduction (rnnoise) | Remove background noise |
| 2 | High-pass Filter | Roll off rumble below 80 Hz |
| 3 | Equalizer | Cut mud, add presence, tame harsh air |
| 4 | Compressor | Even out dynamics |
| 5 | De-esser | Control sibilance |
| 6 | Limiter | Prevent clipping |
| 7 | Auto Gain | Normalize loudness (EBU R128 target) |
| 8 | Stereo Tools | Convert to mid-side for stereo control |

### `configs/OldTimeyRadio_Corrected.json`

[`configs/OldTimeyRadio_Corrected.json`](configs/OldTimeyRadio_Corrected.json)

A vintage AM-radio voice chain. The defining move is a tight 300–3400 Hz bandpass filter, plus light saturation shaping:

| Stage | Plugin | Purpose |
|-------|--------|---------|
| 1 | Noise Reduction (rnnoise) | Remove background noise |
| 2 | High-pass Filter | Cut everything below 300 Hz |
| 3 | Low-pass Filter | Cut everything above 3400 Hz |
| 4 | Equalizer | Shape the midrange for period-accurate body |
| 5 | Auto Gain | Normalize level |
| 6 | Compressor | Glue dynamics, add broadcast density |
| 7 | Bass Enhancer | Add low harmonic warmth |
| 8 | Limiter | Prevent clipping |

> **Note:** The original blog post called this effect "OldTimeyRadio"; the `_Corrected` version is the refined preset.

## Article Summaries

These summaries capture the audio-engineering principles that fed into the presets. They were generated with the `article-summary` skill.

- **[Podcast EQ Settings Guide](docs/202609251000%20-%20Summary%20-%20Podcast%20EQ%20Settings%20Guide.md)** — subtractive EQ, frequency ranges for speech, and starting settings by voice type.
- **[Clear Voice Audio EQ](docs/202609251200%20-%20Summary%20-%20Clear%20Voice%20Audio%20EQ.md)** — the "cut first, boost rarely" philosophy and a complete frequency map for podcast vocals.
- **[Old Radio Voice Effect](docs/202609251500%20-%20Summary%20-%20Old%20Radio%20Voice%20Effect.md)** — the 300–3400 Hz bandpass, filter slopes, and tube-saturation character that define the vintage radio sound.
- **[EasyEffects Notebook Speaker EQ](docs/202609271500%20-%20Summary%20-%20EasyEffects%20Notebook%20Speaker%20EQ.md)** — a bonus reference on using dynamic processing (instead of static EQ) to improve internal notebook speakers.

## How to Use

1. Install [Easy Effects](https://github.com/wwmm/easyeffects) on a PipeWire-based Linux system.
2. Copy a preset JSON file to Easy Effects' preset directory. On most systems:
   - Presets are loaded from `~/.config/easyeffects/input/`
   - Or use **Input → Load Preset** in the GUI.
3. Select the input device you want to process (e.g., your podcasting mic or headset mic).
4. Load `Podcaster` for clean speech, or `OldTimeyRadio_Corrected` for the vintage effect.
5. Listen, then tweak. These are starting points — every mic, voice, and room is different.

## The Larger Pattern

This repo is a concrete example of a general idea: **use AI for transformation tasks in domains where you are not the expert.**

- **Summarize** articles into reusable notes.
- **Translate** documentation into a focused skill.
- **Reformat** a goal + known inputs into a working config file.

The human still owns the questions and the definition of "done." AI is the adapter.

## License

[MIT License](LICENSE)
