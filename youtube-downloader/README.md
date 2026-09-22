# Full-Stack YouTube Downloader Application

A modern, production-grade web application built to analyze and download media streams up to **4K (2160p)** and extract **MP3 audio** from supported YouTube video URLs.

Built with a **React + Vite + TypeScript + Tailwind CSS** frontend and a secure **Node.js + Express + TypeScript** backend leveraging native `yt-dlp` and `FFmpeg`.

---

## Features

- 🎥 **4K Ultra HD & 60fps Support**: Dynamically merges separate 4K video and high-bitrate audio streams into compatible MP4 files using FFmpeg.
- 🎵 **MP3 Audio Extraction**: Extract audio with custom bitrates (320kbps, 256kbps, 192kbps, 128kbps).
- 🔍 **Strict URL Validation**: Built-in SSRF protection permitting only official YouTube hostnames (`youtube.com`, `youtu.be`, `/shorts/`).
- ⚡ **Real-Time Job Tracking**: Polling job manager tracking downloading, stream merging, and file preparation progress.
- 🛡️ **Security & Anti-Abuse**: Uses safe `child_process.spawn` argument arrays (`shell: false`), filename sanitization, rate limiting, and configurable file size limits.
- 🌓 **Dark Mode**: Supports system theme preference default with interactive light/dark mode toggle.

---

## Prerequisites & External Dependencies

The backend application requires **`yt-dlp`** and **`ffmpeg`** installed on your host system PATH.

### 1. Install `yt-dlp`
- **Windows (winget)**: `winget install yt-dlp`
- **Windows (pip)**: `pip install yt-dlp`
- **macOS (Homebrew)**: `brew install yt-dlp`
- **Linux (apt)**: `sudo apt install yt-dlp` or download standalone binary from [yt-dlp releases](https://github.com/yt-dlp/yt-dlp/releases).

### 2. Install `FFmpeg`
- **Windows (winget)**: `winget install Gyan.FFmpeg`
- **macOS (Homebrew)**: `brew install ffmpeg`
- **Linux (apt)**: `sudo apt install ffmpeg`

> 💡 *Note: If binaries are missing on startup, the backend server will start and log setup instructions.*

---

## Installation

### 1. Clone & Install Dependencies

```bash
# Navigate to backend and install
cd youtube-downloader/backend
npm install

# Navigate to frontend and install
cd ../frontend
npm install
```

---

## Development

Start both backend and frontend servers:

### Backend Development Server (Port 5000)

```bash
cd youtube-downloader/backend
npm run dev
```

### Frontend Development Server (Port 5173)

```bash
cd youtube-downloader/frontend
npm run dev
```

Open your browser and navigate to:
```text
http://localhost:5173
```

---

## Production Build & Execution

### Build Backend
```bash
cd youtube-downloader/backend
npm run build
npm start
```

### Build Frontend
```bash
cd youtube-downloader/frontend
npm run build
```
Static production files will be output to `frontend/dist`.

---

## Docker Deployment (Recommended)

Run the full stack with zero host installation of `yt-dlp` or `ffmpeg`:

```bash
docker-compose up --build
```

Access the frontend at `http://localhost:5173`.

---

## Environment Variables

### Backend (`backend/.env`)
- `PORT`: Backend port (default `5000`)
- `MAX_DOWNLOAD_SIZE_GB`: Max permitted video download size (default `10`)
- `JOB_EXPIRATION_MINUTES`: Auto-cleanup timeout for temporary files (default `30`)
- `FRONTEND_URL`: Allowed CORS origin (default `http://localhost:5173`)

### Frontend (`frontend/.env`)
- `VITE_API_URL`: Backend API base URL (default `http://localhost:5000`)

---

## License & Usage Notice

This software is provided for downloading media content that you own or are legally authorized to download. It does not bypass access control mechanisms, DRM, or paywalls.
