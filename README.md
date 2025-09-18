### README.md
```markdown
# Latin Dubber

A desktop application that transforms your videos with Latin subtitles and dubbing using AI.

## Features

- **Video Upload**: Drag & drop MP4 files
- **Audio Transcription**: Uses OpenAI Whisper (local or API)
- **Latin Translation**: HuggingFace MarianMT models or API
- **Subtitle Generation**: Creates SRT files with perfect timing
- **Text-to-Speech**: Optional Latin audio dubbing with Coqui TTS or ElevenLabs
- **Video Processing**: Combines everything using FFmpeg

## Quick Start

### Prerequisites
- Node.js 16+ 
- Python 3.8+
- FFmpeg installed on your system

### Installation

1. **Clone or extract the project**
```bash
mkdir latin-dubber
cd latin-dubber
# Copy all files into this directory
```

2. **Install Frontend Dependencies**
```bash
cd frontend
npm install
```

3. **Install Backend Dependencies**
```bash
cd ../backend
pip install -r requirements.txt
```

4. **Configure API Keys (Optional)**
Edit `config/config.json` and add your API keys:
```json
{
  "api_keys": {
    "openai": "sk-your-openai-key-here",
    "huggingface": "hf_your-huggingface-token-here",
    "elevenlabs": "your-elevenlabs-api-key"
  }
}
```

### Running the Application

1. **Start Backend Server**
```bash
cd backend
python app.py
```

2. **Start Frontend (in new terminal)**
```bash
cd frontend
npm start
```

The application will open in Electron automatically.

## Usage

1. **Upload & Options Tab**
   - Drag & drop your MP4 video file
   - Choose options: Latin subtitles only, or subtitles + dubbing
   - Click "Start Processing"

2. **Processing Tab**
   - Watch real-time progress
   - See each processing step complete

3. **Preview & Export Tab**
   - Download your Latin subtitle (.srt) file
   - Download complete video with Latin dub (if selected)
   - Preview the final result

## Configuration

### Local Models (No API Keys Required)
- **Whisper**: Uses `base` model by default
- **Translation**: Helsinki-NLP/opus-mt-en-la
- **TTS**: Coqui TTS models

### API Models (Require Keys)
- **Whisper**: OpenAI API (higher quality)
- **Translation**: HuggingFace Inference API
- **TTS**: ElevenLabs (more natural voices)

## Testing

A sample 30-second MP4 file is included in `test_files/sample_video.mp4` for immediate testing.

## Troubleshooting

### Common Issues

1. **"FFmpeg not found"**
   - Install FFmpeg: https://ffmpeg.org/download.html
   - Ensure it's in your system PATH

2. **"Module not found" errors**
   - Run `pip install -r requirements.txt` again
   - Check Python version (3.8+ required)

3. **Video processing fails**
   - Ensure input video is a valid MP4
   - Check available disk space
   - Try with a shorter video first

4. **Slow processing**
   - Local models are slower but free
   - API models are faster but require keys
   - Processing time depends on video length

### Performance Tips

- Use API keys for faster processing
- Shorter videos (under 5 minutes) process much faster
- Close other applications to free up memory
- SSD storage helps with I/O intensive operations

## File Structure

```
latin-dubber/
├── frontend/          # Electron + React UI
├── backend/           # Python Flask API
├── config/            # Configuration files
├── output/            # Processed videos and subtitles
├── test_files/        # Sample files for testing
└── README.md          # This file
```

## Development

### Adding New Features
- Frontend components are in `frontend/src/components/`
- Backend handlers are in `backend/models/`
- Video processing utilities in `backend/utils/`

### API Endpoints
- `POST /api/upload` - Upload video file
- `POST /api/process` - Start processing pipeline
- `GET /api/status/<job_id>` - Get processing status
- `GET /api/download/<job_id>/<type>` - Download results

## License

MIT License - Feel free to modify and distribute.

## Contributing

1. Fork the project
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## Support

For issues and questions:
1. Check this README first
2. Look at error messages in the console
3. Try with the sample video file
4. Create an issue with detailed error information
