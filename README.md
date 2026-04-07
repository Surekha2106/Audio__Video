# AI Video Translator & Dubber

An AI-powered Flask web application that automatically translates and dubs videos. It extracts audio, utilizes Vosk machine learning for precise speech-to-text, translates the text, and synthesizes human-like voiceovers using neural TTS. FFmpeg dynamically syncs the new audio to the video and auto-generates localized word-level subtitles.

## 🚀 Features
- **Secure User Authentication**: Full signup, login, and session management using Flask-SQLAlchemy.
- **Offline Speech Recognition**: Uses the **Vosk** ML model to accurately transcribe audio into text with precise word-level timestamps.
- **Language Translation**: Uses `deep-translator` to translate transcribed text into various target languages.
- **Neural Voice Dubbing**: Converts translated text back into human-sounding speech using Microsoft Edge Neural TTS (`edge-tts`). Supports multiple languages with male and female voice variants.
- **Dynamic Time Synchronization**: Automatically scales the video speed using `ffmpeg` to match the exact duration of the new translated AI voiceover.
- **Automated Subtitles**: Generates synchronized `.vtt` subtitle files mapped precisely to the newly translated audio.
- **User Dashboard**: Real-time progress tracking of translation jobs and a history log of previously translated files.

## 🛠 Prerequisites

Before running the application, make sure you have the following installed:
1. **Python 3.8+**
2. **FFmpeg**: Must be installed and added to your system's PATH. This is required for all audio/video extraction and merging tasks.
   - *Windows:* Download from [gyan.dev](https://www.gyan.dev/ffmpeg/builds/) or install via `winget install ffmpeg`.
3. **Vosk Offline Model**: You must download a compatible Vosk speech recognition model.
   - Download the model from [Vosk Models](https://alphacephei.com/vosk/models) (e.g., `vosk-model-en-us-0.22`).
   - Extract it into the root of this project and rename the extracted folder to `VoskModel`.

## ⚙️ Installation

1. **Clone the repository:**
   ```bash
   git clone <your-repository-url>
   cd <repository-directory>
   ```

2. **Set up a virtual environment (Recommended):**
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On Mac/Linux:
   source venv/bin/activate
   ```

3. **Install the required dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## 🎮 Running the Application

1. **Start the Flask server:**
   ```bash
   python project1.py
   ```
2. **Access the Web App:**
   Open your browser and navigate to `http://127.0.0.1:5000/`. You will be prompted to sign up/log in before you can access the dashboard to upload videos.

## 📁 Project Structure

- `project1.py`: The main Flask application containing routes, auth, and the core video processing worker.
- `app.db` / `users.db`: SQLite database storing user authentication data.
- `history.json`: Stores user-specific translation history.
- `VoskModel/`: Directory where the offline speech-to-text ML model lives.
- `uploads/`: Temporary storage for original videos uploaded by users.
- `temp/`: Temporary directory for intermediate processing (extracted audio, TTS `.wav` files).
- `outputs/`: Final storage area containing the translated `.mp4` videos and `.vtt` subtitles.
- `templates/` & `static/`: HTML templates and CSS/JS for the application UI.
