# Voice-to-Slide Generator

A local development application that converts MP4 video files into PowerPoint presentations using speech-to-text transcription and AI-powered slide generation.

## Features

### Core Functionality
- **Upload MP4 Videos**: Drag & drop interface for video file uploads
- **Audio Extraction**: Automatically extracts audio from video files
- **Speech-to-Text**: Uses OpenAI Whisper for accurate transcription
- **AI Slide Generation**: OpenAI GPT generates structured slide content
- **PowerPoint Export**: Creates downloadable .pptx files
- **Real-time Progress**: Live tracking of processing stages
- **Transcript Preview**: Review transcript before slide generation

### Professional Design System
- **4 Professional Themes**: Corporate Blue, Modern Green, Elegant Purple, Professional Gray
- **Visual Theme Selection**: Interactive theme picker with color previews
- **Enhanced Typography**: Professional fonts (Calibri), proper hierarchy, and spacing
- **Slide Numbers & Footers**: Page numbers and presentation titles on every slide
- **Decorative Elements**: Accent lines, shapes, and visual polish
- **Better Formatting**: Improved bullet points, consistent spacing, and alignment
- **Theme-Based Styling**: Consistent colors, backgrounds, and visual elements

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
pip3 install -r requirements.txt

# Create environment file
cp .env.example .env

# Add your OpenAI API key to .env
# Edit the .env file and replace 'your_openai_api_key_here' with your actual API key
# IMPORTANT: Never commit the .env file with your real API key!
```

## ⚠️ Security Note

- **Never commit your `.env` file** - it contains your API key
- The `.gitignore` file is configured to prevent accidental commits of sensitive data
- Keep your OpenAI API key secure and never share it publicly
- The `.env.example` file is safe to commit as it doesn't contain real keys

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
4. **Choose Theme**: Select from 4 professional color themes with visual previews
5. **Generate Slides**: Click "Generate Slides" to create presentation with selected theme
6. **Download**: Click "Download PowerPoint" to get your professionally designed .pptx file

## API Endpoints

- `POST /upload` - Upload MP4 file
- `GET /status/{job_id}` - Check processing status
- `GET /transcript/{job_id}` - Get transcript
- `GET /themes` - Get available presentation themes
- `POST /generate-slides/{job_id}?theme={theme_name}` - Generate slides with selected theme
- `GET /download/{job_id}` - Download PowerPoint

## Professional Slide Design

### Available Themes

1. **Corporate Blue** - Professional business presentations
   - Primary: Deep blue (#197AD2)
   - Background: Light blue (#F0F8FF)
   - Accent: Teal (#009688)
   - Use case: Business meetings, corporate reports

2. **Modern Green** - Fresh, contemporary look
   - Primary: Modern green (#4CAF50)
   - Background: Light green (#F8FFF8)
   - Accent: Orange (#FF9800)
   - Use case: Tech presentations, startups, innovation

3. **Elegant Purple** - Sophisticated and creative
   - Primary: Elegant purple (#9C27B0)
   - Background: Light purple (#FAF5FF)
   - Accent: Gold (#FFC107)
   - Use case: Creative presentations, design reviews

4. **Professional Gray** - Clean, minimal aesthetic
   - Primary: Blue-gray (#607D8B)
   - Background: Light gray (#FAFAFA)
   - Accent: Orange (#FF5722)
   - Use case: Academic presentations, reports

### Design Features

- **Typography**: Professional Calibri font with proper hierarchy
  - Title slides: 36pt bold titles
  - Content slides: 28pt slide titles, 18pt content
- **Slide Numbers**: Bottom-right corner with "current/total" format
- **Footers**: Presentation title in bottom-left (except title slide)
- **Decorative Elements**: 
  - Accent lines under content slide titles
  - Decorative accent bar on title slide
- **Consistent Spacing**: Professional margins and bullet point spacing
- **Theme Colors**: All elements styled with consistent theme colors

### Theme Selection

The frontend provides a visual theme picker where you can:
- Preview color swatches for each theme
- See primary, secondary, and accent colors
- Click to select your preferred theme
- Generate slides with your chosen design

## File Structure

```
project-4/
├── backend/
│   ├── main.py              # FastAPI application with theme system
│   ├── requirements.txt     # Python dependencies
│   ├── .env.example        # Environment template
│   └── temp/               # Temporary file storage
│       ├── uploads/        # Uploaded videos
│       └── outputs/        # Generated presentations
├── frontend/
│   ├── src/
│   │   ├── App.jsx         # Main React component with theme selection
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
pip3 install fastapi uvicorn python-multipart python-pptx moviepy openai openai-whisper python-dotenv

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
- Professional presentation output
- Theme system for design customization

Perfect for testing, prototyping, and local content creation workflows that require professional-quality presentations.

## Output Quality

The generated PowerPoint presentations feature:
- **Professional Design**: Business-ready slides with consistent styling
- **Multiple Themes**: Choose from 4 carefully crafted color schemes
- **Typography**: Proper font hierarchy and spacing
- **Visual Polish**: Slide numbers, footers, and decorative elements
- **Consistent Branding**: Theme-based colors throughout all slides

Transform your audio content into presentation-ready slides that look professionally designed!
