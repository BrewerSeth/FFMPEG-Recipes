# FFMPEG-Recipes
Saved FFMPEG Recipes for managing my media.

A simple copy and paste repo for new FFMPEG recipes. These recipes are designed to work on both MacOS and Linux machines.

## Recipes

### Email-Optimized Video (Share-Ready)

Convert a video to a smaller, email-friendly format. Scales to 720p width, reduces frame rate to 15fps, and removes audio.

```bash
ffmpeg -i input.mp4 -vf scale=720:-2 -r 15 -an -c:v libx264 -crf 30 output.mp4
```

**What it does:**
- `-vf scale=720:-2` - Scales to 720px width, maintains aspect ratio (height rounded to even number)
- `-r 15` - Sets frame rate to 15fps
- `-an` - Removes audio
- `-c:v libx264 -crf 30` - H.264 codec with good compression for smaller file size
