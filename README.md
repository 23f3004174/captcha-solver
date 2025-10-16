# Simple CAPTCHA Solver (Educational Demo)

## Overview
This is a browser-based, self-contained demo that generates very simple, local CAPTCHA images and attempts to solve them using naive computer vision techniques:
- Binarization (thresholding)
- Connected component analysis (to segment glyphs)
- Template matching (with a limited font and rotation set)

Important:
- This app only solves the CAPTCHAs it generates itself. It is not intended for, nor effective at, solving real-world CAPTCHAs.
- Use strictly for educational purposes to learn basic image processing concepts. Do not use this to bypass any third-party security or authentication mechanisms.

## Setup
- No build tools or servers required.
- Open index.html in any modern browser.

## Usage
- Click “New CAPTCHA” to generate a fresh challenge. You can change:
  - Length: number of characters (4–6).
  - Noise: low/medium/high background clutter.
  - Rotations: “Limited set” (angles the solver knows) or “None”.
- Manually solve:
  - Type the characters you see in the input box and click “Verify”.
- Auto-solve:
  - Click “Auto Solve” to run the naive solver. The prediction appears on the right.
  - The overlay highlights detected character bounding boxes.
  - The thresholded (binarized) image is shown to visualize the first processing step.
- Clear:
  - Click “Clear” to reset the canvases and status.

Tips:
- The solver is intentionally simple. It works best with:
  - Limited rotations
  - Low to medium noise
  - The default font
- If the solver prediction doesn’t match, try lowering the noise or disabling rotations.

## Notes
- Everything runs locally in your browser; no data is sent anywhere.
- This demo purposefully avoids supporting external uploads to reinforce safe, educational use only.