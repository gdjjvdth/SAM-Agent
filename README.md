# 🤖 SAM Agent — Autonomous AI Engineering Agent on Android

**SAM Agent** is a full-stack, autonomous software-engineering AI agent running locally and natively on Android. It bridges a local Python engine, PRoot Linux environment, and Android native capabilities to design, build, test, and deploy software directly on your phone.

---

## ✨ Key Features

- ⚡ **Local Autonomous Agent Engine**: Runs an AI coding agent with full workspace isolation, file operations, web search, code refactoring, and multi-step execution loops.
- 📱 **Native Android Terminal & UI**: Built-in VT100 interactive terminal with real-time command suggestions, quick shortcut buttons, and session persistence.
- 🔓 **Full Device & Magisk/KernelSU Root Access**: Unrestricted capabilities to interact with PRoot environments, host Termux, and real Android root commands (`su` / `sam root`).
- 🌐 **Automated Localhost & Port Management**: Auto-frees leftover ports, spins up local testing servers, and verifies live web apps with advanced `http_check`.
- 🌍 **Multilingual & System Auto-Detection**: Supports English, Arabic (العربية), French (Français), Hindi (हिन्दी), and Brazilian Portuguese (Português do Brasil) with automatic device-language matching.

---

## 📥 Installation

1. Download **`SAMAgent.apk`** from the **Assets** section below.
2. Install the APK on your Android device (Enable *"Install from unknown sources"* if prompted).
3. Open **SAM Agent** and grant requested permissions.
4. The app will initialize the engine and PRoot environment automatically on first launch.

---

## 🚀 Usage Guide

### 1. Starting a Conversation & Workspace
- Open the app to launch a dedicated, isolated workspace.
- Provide instructions in natural language:
  - *"Build a responsive modern Pomodoro web application and start a preview server."*
  - *"Inspect /system/build.prop and check device properties using root."*
  - *"Write a Python script to scrape and format local news data."*

### 2. Live Web Previews & Localhost Testing
- When SAM starts a web server, tap the generated `http://localhost:8000/` link to test the live application directly in your browser.
- SAM automatically tests asset loading (CSS/JS), verifies syntax, and confirms page content before completing the task.

### 3. Using the Interactive Terminal
- Open the side menu and tap **Terminal** to access the PRoot shell.
- Use the **Suggestion Bar** above the keyboard for instant command auto-completion (`git`, `python3`, `pkg`, `npm`, `su`, etc.).

### 4. Language & System Settings
- Navigate to **Settings** (⚙️) from the drawer:
  - **Interface Language**: Switch between *Auto (System Language)*, English, العربية, Français, हिन्दी, or Português.
  - **Environment Mode**: Toggle between Native PRoot Linux and Termux bridging.
  - **Root Mode**: Enable superuser commands for deep system automation via Magisk/KernelSU.

---

## 🛡️ Security & Privacy
- Zero cloud tracking of your local workspace files.
- Safe port cleanup and isolated workspace folders for each conversation.
