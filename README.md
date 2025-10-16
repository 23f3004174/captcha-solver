# CAPTCHA Generator & Verification (Ethical Demo)

## Overview
This web app demonstrates how to generate and verify simple CAPTCHAs in the browser using HTML5 Canvas for image challenges and an accessible math alternative. It intentionally does not include any automated CAPTCHA breaking or “solver” functionality. Building or distributing tools to bypass third‑party CAPTCHA systems can be harmful and is not supported.

What you’ll see:
- Image CAPTCHA with randomized characters, rotation, noise, and interference lines.
- Accessible alternative: a simple math question.
- Client-side verification of the user’s input (pair with server-side checks in real deployments).

## Setup
- No build steps or dependencies.
- Download the repository (or just the files) and open `index.html` in any modern browser.

## Usage
1. Open `index.html`.
2. Choose your challenge type:
   - Image CAPTCHA (default), or
   - Accessible Math (toggle using the switch at the top).
3. Enter the characters you see (image mode) or the result to the math question (accessible mode).
4. Click Verify (or press Enter) to check your answer.
5. Use Refresh to generate a new challenge. Use Peek to reveal the current answer for testing only.

Notes:
- This is a client-only demo; for production, add server-side generation and verification to prevent tampering.
- Avoid exposing plaintext challenges in the DOM; render them onto a canvas or generate server-side images.
- Consider rate limiting, rotating challenges, and additional bot mitigation strategies beyond CAPTCHAs.