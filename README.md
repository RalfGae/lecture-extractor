# DummyEnv
DummyEnv: Quick AI Project Starter

## Overview
This repository provides a simple terminal-based chatbot using OpenAI's API. It is designed for fast setup and experimentation with AI chat models.

## Features
- Chatbot powered by OpenAI (GPT-4o-mini)
- Easy setup with a shell script
- Uses environment variables for API keys

## Files
- `lesson-3.py`: Main chatbot script
- `requirements.txt`: Python dependencies
- `setup.sh`: Setup script for virtual environment and dependencies

## Setup
1. **Clone this repository**
2. **Run the setup script:**
   ```bash
   bash setup.sh
   ```
3. **Set your OpenAI API key:**
   - Create a `.env` file in the project root with:
     ```
     OPENAI_API_KEY=your-api-key-here
     ```
4. **Activate the virtual environment:**
   ```bash
   source venv/bin/activate
   ```

## Usage
Run the chatbot:
```bash
python3 lesson-3.py
```
Type your message and interact with the bot. Type `exit`, `bye`, or `quit` to end the session.

## Dependencies
- openai
- python-dotenv

## License
MIT (or specify your license)
