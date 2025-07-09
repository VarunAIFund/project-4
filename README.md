# Voice-to-Slide Generator

A local development application that converts MP4 video files into PowerPoint presentations using speech-to-text transcription and AI-powered slide generation.

## Features

- **Upload MP4 Videos**: Drag & drop interface for video file uploads
- **Audio Extraction**: Automatically extracts audio from video files
- **Speech-to-Text**: Uses OpenAI Whisper for accurate transcription
- **AI Slide Generation**: OpenAI GPT generates structured slide content
- **PowerPoint Export**: Creates downloadable .pptx files
- **Real-time Progress**: Live tracking of processing stages
- **Transcript Preview**: Review transcript before slide generation

## Tech Stack

### Frontend
- React 18 with Vite
- Tailwind CSS for styling
- React Dropzone for file uploads
- Axios for API communication

### Backend
- FastAPI (Python)
- OpenAI Whisper (local installation)
- OpenAI GPT API
- python-pptx for PowerPoint generation
- moviepy for video processing

## Prerequisites

- Node.js 18+ and npm
- Python 3.8+
- OpenAI API key
- FFmpeg (for video processing)

## Installation

### 1. Clone and Setup

```bash
cd project-4
```

### 2. Backend Setup

```bash
cd backend

# Install Python dependencies
pip install -r requirements.txt

# Create environment file
cp .env.example .env

# Add your OpenAI API key to .env
echo "OPENAI_API_KEY=your_api_key_here" > .env
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install
```

## Running the Application

### Start Backend (Terminal 1)

```bash
cd backend
uvicorn main:app --reload
```

Backend will run on `http://localhost:8000`

### Start Frontend (Terminal 2)

```bash
cd frontend
npm run dev
```

Frontend will run on `http://localhost:3000`

## Usage

1. **Upload Video**: Drag & drop an MP4 file or click to select
2. **Process Audio**: Click "Process Audio" to extract and transcribe
3. **Review Transcript**: Preview the generated transcript
4. **Generate Slides**: Click "Generate Slides" to create presentation
5. **Download**: Click "Download PowerPoint" to get your .pptx file

## API Endpoints

- `POST /upload` - Upload MP4 file
- `GET /status/{job_id}` - Check processing status
- `GET /transcript/{job_id}` - Get transcript
- `POST /generate-slides/{job_id}` - Generate slides
- `GET /download/{job_id}` - Download PowerPoint

## File Structure

```
project-4/
├── backend/
│   ├── main.py              # FastAPI application
│   ├── requirements.txt     # Python dependencies
│   ├── .env.example        # Environment template
│   └── temp/               # Temporary file storage
│       ├── uploads/        # Uploaded videos
│       └── outputs/        # Generated presentations
├── frontend/
│   ├── src/
│   │   ├── App.jsx         # Main React component
│   │   ├── main.jsx        # React entry point
│   │   └── index.css       # Tailwind CSS
│   ├── package.json        # Node dependencies
│   ├── vite.config.js      # Vite configuration
│   └── tailwind.config.js  # Tailwind configuration
└── README.md               # This file
```

## Development Notes

- **Local Only**: Designed for local development, no production deployment
- **No Authentication**: Simple localhost-to-localhost communication
- **File Cleanup**: Temporary files stored in `backend/temp/` directories
- **Console Logging**: Debug output available in browser console and terminal
- **CORS Enabled**: Configured for localhost:3000 ↔ localhost:8000

## Troubleshooting

### Common Issues

1. **FFmpeg not found**: Install FFmpeg for video processing
2. **OpenAI API errors**: Check API key in `.env` file
3. **File upload fails**: Ensure backend is running on port 8000
4. **Whisper model loading**: First run downloads model automatically

### Dependencies

Make sure all required packages are installed:

```bash
# Backend
pip install fastapi uvicorn python-multipart python-pptx moviepy openai openai-whisper

# Frontend
npm install react react-dom axios react-dropzone
```

## Local Development Focus

This application is optimized for local development with:
- Fast hot-reload with Vite
- Simple file-based storage
- Console debugging
- No security overhead
- Quick iteration cycles

Perfect for testing, prototyping, and local content creation workflows.# project-4
