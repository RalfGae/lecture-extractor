# lecture-extractor

Extract slides and time-aligned transcripts from recorded lectures and presentations.

## What it does

This tool takes a recorded video lecture or presentation and produces:

- **Unique slide images** — duplicate frames are filtered out, keeping only actual slide transitions
- **Time-stamped transcript** — full speech-to-text transcription with timestamps via OpenAI Whisper
- **Slide–transcript alignment** — each extracted slide is paired with the corresponding section of the transcript, preserving the relationship between what was shown and what was said

The output is a set of slide images with their matching transcript segments, ready for review, archiving, or further processing.

## Pipeline

1. **Download** — Retrieve the video stream (supports HLS/m3u8 via yt-dlp)
2. **Transcribe** — Generate time-stamped subtitles using Whisper (runs locally on GPU)
3. **Extract slides** — Sample video frames at regular intervals and deduplicate using perceptual hashing
4. **Align** — Map transcript segments to slides based on matching timestamps

## Requirements

- Python 3.12+
- ffmpeg
- A GPU with ≥ 8 GB VRAM (recommended for Whisper large-v3)

## Setup

**Quick setup (recommended):**
```bash
git clone https://github.com/RalfGae/lecture-extractor.git
cd lecture-extractor
bash setup.sh  # Creates venv, installs all dependencies from requirements.txt
source venv/bin/activate
```

**Manual setup (if you prefer individual commands):**
```bash
git clone https://github.com/RalfGae/lecture-extractor.git
cd lecture-extractor
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt  # Installs: yt-dlp, openai-whisper, imagehash, Pillow, openai, python-dotenv
sudo apt install ffmpeg  # if not already installed
```

## Current Status

This project is in early development. Currently contains:
- `lesson-3.py`: Development/testing chatbot for OpenAI API integration
- Basic project structure and setup scripts

The main lecture extraction functionality is planned for future implementation.

## License

MIT
