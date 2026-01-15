# Automated Notepad Data Entry Bot (Desktop Automation)

## Project Overview

This project is a **Python-based desktop automation bot** that fetches blog posts from the **JSONPlaceholder API** and automatically writes each post into **separate text files using Windows Notepad**.

The bot uses **computer vision, screenshot analysis, mouse/keyboard automation, and fallback strategies** to reliably locate the Notepad icon **anywhere on the desktop**, even when using **busy wallpapers** or **dark/light themes**.

---

## Key Capabilities

- Detects the **Notepad icon anywhere on the desktop**
- Dynamically calculates the **exact screen coordinates** of the icon
- Works with:
  - Busy or textured wallpapers
  - Dark mode and light mode
- Fully automated typing and saving
- Multiple fallback strategies for reliability

---

## Features

- Fetches blog posts from **JSONPlaceholder API**
- Automatically launches **Windows Notepad**
  - Desktop icon detection using **OpenCV**
  - Multi-scale template matching
  - Screenshot-based analysis
  - Fallback launch via **Win + R**
- Types formatted blog content:
  - Title
  - Body
- Saves each post as an individual `.txt` file
- Automatically handles file overwrite confirmations
- Saves annotated screenshots for debugging
- Processes a configurable number of posts (default: first 10)

---

## Target Environment

- **Operating System:** Windows 10 / Windows 11
- **Screen Resolution:** 1920 × 1080
- **Desktop Capabilities:**
  - Screenshot capture
  - Mouse & keyboard control
  - Image processing

---

## How Icon Detection Works

1. Captures a full desktop screenshot
2. Converts image to grayscale
3. Applies edge detection (Canny)
4. Performs **multi-scale template matching**
5. Detects the icon even if:
   - Desktop background is busy
   - Dark or light theme is used
6. Calculates the icon’s center coordinates
7. Moves the mouse and double-clicks to open Notepad
8. Saves annotated screenshots for verification

---

## Error Handling & Robustness

The bot includes strong error handling for the following cases:

### Desktop & Icon Detection
- Icon not found on desktop
- Multiple matching icons detected
- Icon partially obscured by windows
- Desktop background affects detection
- Retry logic:
  - Up to **3 attempts**
  - **1-second delay** between retries

### Application Launch
- Validates that Notepad actually launched by:
  - Window title verification
  - Timeout-based checks
- Fallback to **Win + R → notepad.exe** if icon detection fails

### API & Data Handling
- Graceful degradation if API is unavailable
- Browser-based fallback to fetch JSON data
- Clipboard-based data extraction as backup

### File Handling
- Detects existing files in the target directory
- Automatically confirms file replacement dialogs
- Verifies that files are saved successfully

---

## Requirements

- **Python 3.7+**
- **Windows OS**
- Active desktop session
- Recommended: Virtual environment

---

## Installation

### Clone the Repository
```bash
git clone <repository-url>
cd <project-folder>
```

### Create and Activate a Virtual Environment
```bash
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### Install Dependencies
```bash
pip install .
```
