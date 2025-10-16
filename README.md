# CAPTCHA OCR Solver (FastAPI + Tesseract)

## Overview
This is a minimal FastAPI web application that solves CAPTCHA images using Tesseract OCR via pytesseract. It provides:
- A REST endpoint POST /solve that accepts an image file and returns detected text as JSON.
- A simple web UI at GET / for uploading an image and viewing OCR results.
- Basic preprocessing options to improve OCR accuracy on noisy CAPTCHAs.

Key technologies:
- FastAPI for the API and serving the UI
- Pillow (PIL) for image handling and preprocessing
- Tesseract OCR engine via pytesseract

## Setup

Prerequisites:
- Python 3.9+ recommended
- Tesseract OCR engine installed on your system

1) Install Tesseract OCR engine:

- macOS (Homebrew):
  - brew install tesseract

- Ubuntu/Debian:
  - sudo apt-get update
  - sudo apt-get install -y tesseract-ocr

  Optional language packs (example):
  - sudo apt-get install -y tesseract-ocr-eng tesseract-ocr-osd

- Windows:
  - Download installer from: https://github.com/UB-Mannheim/tesseract/wiki
  - Install and ensure the Tesseract install directory (e.g., C:\Program Files\Tesseract-OCR) is added to your PATH.
  - You may need to set pytesseract.pytesseract.tesseract_cmd to the tesseract.exe path if not on PATH.

2) Create and activate a virtual environment (optional but recommended):
- python -m venv .venv
- On macOS/Linux: source .venv/bin/activate
- On Windows: .venv\Scripts\activate

3) Install Python dependencies:
- pip install fastapi uvicorn pillow pytesseract

## Usage

Start the server:
- uvicorn index:app --reload

Open the UI:
- Visit http://127.0.0.1:8000/ to upload an image and see OCR results.

API usage:

- Endpoint: POST /solve
- Form fields:
  - image: file (required) — the CAPTCHA image
  - preprocess: string (optional) — one of auto, none, binary, median, contrast (default: auto)
  - psm: string/int (optional) — Tesseract page segmentation mode, e.g., 7, 8, 6, 13 (default: 7)
  - lang: string (optional) — language code(s), e.g., eng (default), deu, spa

Example curl:
- curl -X POST http://127.0.0.1:8000/solve \
  -F "image=@captcha.png" \
  -F "preprocess=auto" \
  -F "psm=7" \
  -F "lang=eng"

Typical JSON response:
{
  "text": "AB12C",
  "avg_confidence": 87.34,
  "psm": 7,
  "language": "eng",
  "preprocess": "auto",
  "tesseract_version": "5.3.3"
}

Health check:
- GET /health returns JSON indicating whether Tesseract is available.

Notes and tips:
- For best CAPTCHA results, try different PSM values (7 for a single line, 8 for a single word, 13 for raw line).
- Preprocessing can greatly help. Start with auto, then try binary or median for noisy images.
- Ensure Tesseract is installed and discoverable in PATH. If not, you may need to set:
  - In code: pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe" (Windows)
- Additional language packs may be needed for non-English CAPTCHAs.