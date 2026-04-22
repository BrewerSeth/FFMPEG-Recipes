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

### Teams-Optimized Video (High Quality)

Convert a video to higher quality for Microsoft Teams sharing. Scales to 1920p width, 30fps, and includes audio.

```bash
ffmpeg -i input.mp4 -vf scale=1920:-2 -r 30 -c:v libx264 -crf 23 output.mp4
```

**What it does:**
- `-vf scale=1920:-2` - Scales to 1920px width, maintains aspect ratio (height rounded to even number)
- `-r 30` - Sets frame rate to 30fps (smooth playback)
- `-c:v libx264 -crf 23` - H.264 codec with higher quality (lower CRF = better quality)
- Audio is preserved for better quality communication

### Teams-Optimized Screen Recording (Fast)

Convert a Mac screen recording to double speed, 15fps, and 1080p height for Teams sharing.

```bash
ffmpeg -i input.mov -vf "setpts=0.5*PTS,scale=-2:1080" -r 15 -c:v libx264 -crf 23 output.mp4
```

**What it does:**
- `setpts=0.5*PTS` - Doubles the playback speed
- `scale=-2:1080` - Sets height to 1080px, maintains aspect ratio (width rounded to even number)
- `-r 15` - Sets frame rate to 15fps
- `-c:v libx264 -crf 23` - H.264 codec with high quality for Teams sharing

