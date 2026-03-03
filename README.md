# skill-tiktok-ads-video

Generate TikTok-style short-form ad videos with animated pill captions. Takes a base MP4, overlays animated captions with fade in/out, mixes background audio. Built-in product presets — no captions JSON file needed.

## Usage

```bash
uv run --with moviepy --with pillow scripts/overlay.py \
  --video base.mp4 \
  --output final.mp4 \
  --product rain_cloud \
  --style subtitle_talk
```

## Built-in Products

| ID | Product |
|---|---|
| `rain_cloud` | Rain Cloud Humidifier |
| `hydro_bottle` | Hydrogen Water Bottle |
| `mini_cam` | Mini Clip Camera |

## Styles

- `phrase_slam` — Bold full-screen phrase drops
- `subtitle_talk` — Subtitle-style bottom captions
- `bullet_reveal` — Feature bullets revealed one by one

## Requirements

- Python 3.10+ with `uv`
- `ffmpeg` installed

## Part of the [Zero2Ai-hub](https://github.com/Zero2Ai-hub) skills ecosystem.
