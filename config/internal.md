# Internal Config — skill-tiktok-ads-video
# Tech1Mart / Zeerotoai Operations

## Font paths
```
/home/aladdin/.local/share/fonts/Montserrat-Black.ttf
/home/aladdin/.local/share/fonts/Montserrat-Bold.ttf
```

## Audio library
```
/home/aladdin/.openclaw/workspace/audio_Hyperfun.mp3   ← TikTok-safe beat, use at 0.5 vol, start at 8s
```

## Veo 3.1 base video output path
```
/home/aladdin/.openclaw/workspace/<YYYY-MM-DD>-veo-<product>.mp4
```

## Run command
```bash
uv run --with moviepy --with pillow \
  /home/aladdin/.openclaw/workspace/skills/skill-tiktok-ads-video/scripts/overlay.py \
  --video /home/aladdin/.openclaw/workspace/2026-02-28-veo-hydro.mp4 \
  --output /home/aladdin/.openclaw/workspace/2026-02-28-veo-hydro-final.mp4 \
  --captions /home/aladdin/.openclaw/workspace/skills/skill-tiktok-ads-video/scripts/example_captions.json \
  --audio /home/aladdin/.openclaw/workspace/audio_Hyperfun.mp3 \
  --audio-start 8 \
  --audio-vol 0.5
```

## Active product captions (Tech1Mart)

### Rain Cloud Humidifier (77261)
- Price: 129 AED
- Hook: "POV: your room is dry af"
- Claim: "this cloud humidifier / hits different"
- CTA: "129 AED / Free delivery UAE / Link in bio"
- Captions: `config/captions_rain_cloud.json`

### Hydrogen Water Bottle (77262)
- Price: 149 AED
- Hook: "POV: you said you'd / drink more water"
- Claim: "hydrogen water / hits different"
- CTA: "149 AED / Free delivery UAE / Link in bio"
- Captions: `scripts/example_captions.json`

### Mini Clip Camera (77263)
- Price: 99 AED
- Hook: "POV: you want to / record everything"
- Claim: "mini clip camera / goes anywhere"
- CTA: "99 AED / Free delivery UAE / Link in bio"
- Captions: `config/captions_mini_cam.json` (TBD)

## TikTok account
- Handle: @tech1mart (or product-specific)
- Post pipeline: generate video → send to Dropship Ops → manual post or TikTok API (pending Advertiser ID)

## Color palette (brand standard)
- Cyan/electric: `[0, 195, 255]`
- Gold/CTA: `[255, 210, 0]`
- White pill: `[255, 255, 255]`
- Black pill: `[0, 0, 0]`

## Known issues
- NotoColorEmoji fails with PIL at arbitrary sizes — use text alternatives (no emoji in captions)
- PIL textbbox y-offset bug fixed in `pill()` function — do NOT rewrite without keeping the offset compensation

## Video generation pipeline
1. Veo 3.1 → base video (`veo3-video-gen` skill)
2. `overlay.py` → add captions + audio
3. Review in Dropship Ops group
4. Post to TikTok (manual until Advertiser ID obtained)
