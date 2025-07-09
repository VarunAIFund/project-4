# Voice-to-Slide Generator - Backend

FastAPI backend for the Voice-to-Slide Generator application.

## Quick Start

```bash
pip install -r requirements.txt
cp .env.example .env
# Add your OpenAI API key to .env
uvicorn main:app --reload
```

API will be available at `http://localhost:8000`

## Features

- **File Upload**: Accepts MP4 video files
- **Audio Extraction**: Uses moviepy to extract audio from video
- **Speech-to-Text**: OpenAI Whisper for transcription
- **AI Slide Generation**: OpenAI GPT for structured content
- **PowerPoint Creation**: python-pptx for .pptx file generation
- **Job Tracking**: In-memory job status management
- **CORS Support**: Configured for localhost:3000

## API Endpoints

### `POST /upload`
Upload MP4 file and get job ID
- **Input**: MP4 file (multipart/form-data)
- **Output**: `{"job_id": "uuid", "message": "success"}`

### `GET /status/{job_id}`
Check processing status
- **Output**: `{"status": "...", "progress": 0-100, ...}`

### `GET /transcript/{job_id}`
Get or generate transcript
- **Output**: `{"transcript": "..."}`

### `POST /generate-slides/{job_id}`
Generate PowerPoint slides
- **Output**: `{"message": "success", "slide_content": {...}}`

### `GET /download/{job_id}`
Download generated PowerPoint file
- **Output**: Binary .pptx file

## Processing Pipeline

1. **Upload**: Store MP4 file in `temp/uploads/`
2. **Audio Extraction**: Use moviepy to extract audio as WAV
3. **Transcription**: Process audio with Whisper model
4. **Slide Generation**: Send transcript to OpenAI GPT
5. **PowerPoint Creation**: Generate .pptx with python-pptx
6. **Download**: Serve file from `temp/outputs/`

## Configuration

### Environment Variables

Create `.env` file with:
```
OPENAI_API_KEY=your_openai_api_key_here
```

### Dependencies

- **FastAPI**: Web framework
- **Whisper**: Speech-to-text (local model)
- **OpenAI**: GPT API for slide generation
- **python-pptx**: PowerPoint file creation
- **moviepy**: Video/audio processing
- **uvicorn**: ASGI server

## Job Status Flow

```
uploaded → extracting_audio → transcribing → transcript_ready → generating_slides → creating_powerpoint → completed
```

## File Storage

- **Uploads**: `backend/temp/uploads/{job_id}.mp4`
- **Audio**: `backend/temp/uploads/{job_id}.wav`
- **Output**: `backend/temp/outputs/{job_id}.pptx`

## Error Handling

- File validation (MP4 only)
- API error responses
- Job status error tracking
- Console logging for debugging

## Development Notes

- **Local Only**: Designed for localhost development
- **No Authentication**: Simple local API
- **In-Memory Jobs**: No persistent storage
- **Console Logging**: Debug output enabled
- **CORS**: Configured for React frontend