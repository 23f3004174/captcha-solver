# Overview
This is a small, client-side web app that performs Optical Character Recognition (OCR) on images entirely in your browser using Tesseract.js. It allows you to load an image, apply helpful pre-processing (scale, threshold, invert), and extract text. The app also visualizes detected word regions.

Important: This tool is intended for ethical, legitimate OCR tasks (e.g., digitizing documents you own). It is not intended for, and should not be used to bypass access-control mechanisms such as CAPTCHAs or other anti-bot challenges.

# Setup
No build steps required.

- Option 1: Open index.html directly in a modern browser with internet access (to download OCR model files).
- Option 2: Serve it locally (recommended for best compatibility):
  - Python: `python -m http.server 8080` then open http://localhost:8080
  - Node: `npx http-server -p 8080` then open http://localhost:8080

The app uses Tesseract.js via CDN. The OCR runs locally in your browser; no images are uploaded to any server.

# Usage
- Click “Choose Image” or drag & drop an image into the drop zone.
- Adjust options:
  - Scale: Upscales the image before OCR (higher can improve accuracy).
  - Threshold: Binarizes the image (helpful for noisy or low-contrast text). Set to off (0) to disable.
  - Invert: For light text on dark background images.
- Click “Run OCR” to extract text.
- The “OCR Regions” pane highlights recognized words (with reasonable confidence).
- Copy results via the “Copy” button.

Tips:
- For best results, crop the image to the region of interest and ensure the text is reasonably sharp.
- Try Scale between 1.8–2.4 and Threshold around 120–180 for many scanned images.

Ethical use reminder: Do not use OCR to circumvent CAPTCHAs or other anti-bot systems.