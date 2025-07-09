# Voice-to-Slide Generator - Frontend

React frontend for the Voice-to-Slide Generator application.

## Quick Start

```bash
npm install
npm run dev
```

Application will be available at `http://localhost:3000`

## Features

- **Drag & Drop Upload**: Simple MP4 file upload interface
- **Real-time Progress**: Visual progress bar and status updates
- **Transcript Preview**: Review generated transcript before slides
- **Slide Content Preview**: Preview generated slide structure
- **Download Interface**: One-click PowerPoint download
- **Error Handling**: User-friendly error messages
- **Responsive Design**: Works on desktop and mobile

## Tech Stack

- React 18 with Vite
- Tailwind CSS for styling
- React Dropzone for file uploads
- Axios for API communication

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

### Configuration

- **API Base URL**: `http://localhost:8000`
- **Port**: 3000 (configured in `vite.config.js`)
- **Hot Reload**: Enabled by default

## Usage Flow

1. User uploads MP4 file via drag & drop
2. File is sent to backend API
3. Progress bar shows processing stages
4. Transcript is displayed for review
5. Generated slides are previewed
6. PowerPoint file is downloaded

## API Integration

The frontend communicates with the FastAPI backend through these endpoints:

- `POST /upload` - File upload
- `GET /status/{job_id}` - Status polling
- `GET /transcript/{job_id}` - Transcript retrieval
- `POST /generate-slides/{job_id}` - Slide generation
- `GET /download/{job_id}` - File download

## Styling

Uses Tailwind CSS for rapid development:
- Responsive design
- Clean, modern interface
- Accessible color scheme
- Hover states and transitions