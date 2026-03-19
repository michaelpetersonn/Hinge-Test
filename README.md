# Hinge Profile Builder — PowerPoint Night Edition

A browser-based tool for creating fake Hinge dating profiles for your friends. Perfect for PowerPoint Night presentations.

## Quick Start

### Prerequisites

- **Python 3** — used only to serve the file locally
  - **Mac**: Pre-installed. Verify with `python3 --version`
  - **Windows**: Download from [python.org](https://www.python.org/downloads/)
- A modern browser (Chrome, Safari, Edge, Firefox)

### Running the App

1. Open a terminal (Mac) or Command Prompt (Windows) and navigate to this project folder:

   ```bash
   cd path/to/hinge-profile-builder
   ```

2. Start a local web server:

   ```bash
   python3 -m http.server 8765
   ```

   On Windows, if `python3` doesn't work, try:

   ```bash
   python -m http.server 8765
   ```

3. Open your browser and go to:

   ```
   http://localhost:8765/index.html
   ```

4. You're in! Start building profiles.

> **Why a local server?** The app uses `html2canvas` for screenshots, which requires HTTP — opening the file directly via `file://` will cause security restrictions.

## How to Use

### 1. Fill in Profile Info

The left panel contains all the editable fields:

- **Name & Age** — displayed in the phone header and info pills
- **Gender** — Male, Female, or Nonbinary
- **Orientation & Height** — optional detail pills
- **Verified Badge** — toggle the purple checkmark next to the name
- **Job, School, Location** — shown in the details list with icons
- **Religion & Politics** — dropdown selections
- **Dating Intention** — what they're "looking for" with an optional personal note

### 2. Add Photos

- Click any of the 6 photo upload slots to add images
- Photos appear in the phone preview with rounded corners
- Click the **x** on a slot to remove a photo

### 3. Add Prompts

- Choose from 40+ real Hinge prompts via the dropdown, or select **"Write your own..."** to create a custom question
- Write the answer in the text field below
- Optionally upload a photo to each prompt for extra context

### 4. Take Screenshots

The app offers multiple ways to capture the profile:

| Button | What it does |
|---|---|
| **Copy Current View** | Copies the currently visible section of the phone to your clipboard |
| **Download View** / **Download with Frame** | Downloads the current visible section as a PNG |
| **Full Profile** / **Download Full Profile** | Downloads the entire scrollable profile as one tall image |

> **Tip:** Scroll the phone preview to different sections (photo, prompts, details) and use "Copy Current View" to grab each part separately for your slides.

### 5. Reset

Click **Reset Profile** to clear all fields and start fresh for the next friend.

## Troubleshooting

### "Address already in use" error

Another process is already using port 8765. Either:

- **Use it** — the server may already be running. Just open `http://localhost:8765/index.html` in your browser.
- **Kill the old process and restart (Mac/Linux):**

  ```bash
  lsof -ti:8765 | xargs kill -9
  python3 -m http.server 8765
  ```

- **Or pick a different port:**

  ```bash
  python3 -m http.server 9000
  ```

  Then open `http://localhost:9000/index.html` instead.

### Page won't load / connection refused

1. Make sure the terminal is still running the `python3 -m http.server` command — don't close it.
2. Confirm you're in the right directory. Run `ls` (Mac/Linux) or `dir` (Windows) and you should see `index.html` in the output.
3. Try `http://127.0.0.1:8765/index.html` instead of `localhost`.

### Blank page or broken layout

- **Hard refresh** your browser: **Cmd + Shift + R** (Mac) or **Ctrl + Shift + R** (Windows).
- Make sure you're opening via `http://localhost:...` and **not** via `file:///...` in the URL bar.

### Screenshots / copy to clipboard not working

- Must be served over HTTP (localhost), not opened as a file.
- Clipboard copy requires a secure context — `localhost` counts, but `file://` does not.
- If copy still fails, use the **Download** buttons instead.

## Technology

| Component | Technology |
|---|---|
| **Structure** | Single-file HTML5 application (`index.html`) |
| **Styling** | Vanilla CSS3 with CSS custom properties |
| **Logic** | Vanilla JavaScript (no frameworks) |
| **Font** | [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts |
| **Screenshots** | [html2canvas 1.4.1](https://html2canvas.hertzen.com/) via CDN |
| **Icons** | Inline SVGs |
| **Local Server** | Python 3 `http.server` module |

No build step. No dependencies to install. Just one HTML file and a local server.
