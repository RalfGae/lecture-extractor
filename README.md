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
- Project structure and automated setup scripts  
- Core dependencies for video processing, transcription, and image analysis
- Development environment with API integration capabilities

The main lecture extraction functionality is planned for future implementation.

## Version & Draft Roadmap

### Version 0.1.0 (Current)
- [x] ✅ Project setup and documentation
- [x] ✅ Automated environment setup (`setup.sh`)  
- [x] ✅ Core dependencies installed and verified:
  - yt-dlp (video download)
  - OpenAI Whisper (transcription)
  - ImageHash + Pillow (image processing)
  - Development tools (OpenAI API, python-dotenv)
- [x] ✅ Environment tested and functional

### Version 0.2.0 (Planned)
- [ ] 📹 Basic video download functionality (HLS/m3u8 support)
- [ ] 🎤 Audio extraction and Whisper transcription
- [ ] 📄 Time-stamped transcript generation

### Version 0.3.0 (Planned)
- [ ] 🖼️  Frame extraction at regular intervals
- [ ] 🔍 Slide deduplication using perceptual hashing
- [ ] 📊 Basic slide-transcript alignment

### Version 1.0.0 (Target)
- [ ] 🚀 Complete pipeline integration
- [ ] 📋 CLI interface for batch processing
- [ ] 📖 Advanced output formatting
- [ ] 🧪 Comprehensive testing suite

## License

MIT
