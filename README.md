# 🤖 SAM Agent (Beta) — Autonomous AI Software Engineering System for Android

[![GitHub Release](https://img.shields.io/github/v/release/gdjjvdth/SAM-Agent?style=for-the-badge&color=2563eb)](https://github.com/gdjjvdth/SAM-Agent/releases/latest)
[![Status](https://img.shields.io/badge/Status-Public_Beta-yellow.svg?style=for-the-badge)](https://github.com/gdjjvdth/SAM-Agent)
[![Platform](https://img.shields.io/badge/Platform-Android_7.0+-10b981.svg?style=for-the-badge&logo=android)](https://github.com/gdjjvdth/SAM-Agent)
[![License](https://img.shields.io/badge/License-MIT-8b5cf6.svg?style=for-the-badge)](https://github.com/gdjjvdth/SAM-Agent)
[![Direct Download](https://img.shields.io/badge/Direct_Download-SAMAgent.apk-f97316?style=for-the-badge&logo=android)](https://github.com/gdjjvdth/SAM-Agent/releases/download/v1.0.0/SAMAgent.apk)

> ⚠️ **Public Beta Notice**: SAM Agent is currently in active **Beta** testing. Features and execution environments are fully functional, but you may occasionally encounter edge cases. Feel free to report issues and suggestions to help improve future builds!

---

**SAM Agent** is a full-stack, autonomous software engineering agent engineered specifically for Android devices. Unlike simple API wrappers or chat clients, SAM hosts an entire local execution runtime on your phone — combining a self-contained Linux PRoot environment, an autonomous ReAct loop, direct Magisk/KernelSU root capabilities, and native Android hardware bridges.

---

## 🏗️ Core Architecture & Capabilities

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        SAM Agent (Beta - Android)                       │
├────────────────────────────────┬────────────────────────────────────────┤
│         Android Layer          │              Engine Layer              │
│  - Native Java/Kotlin UI       │  - Autonomous ReAct Agent Loop         │
│  - VT100 Interactive Terminal  │  - Tool-Calling & Sandbox Controller   │
│  - PhoneBridge (Sensors/IO)    │  - Workspace Isolation (Git Checkpoints│
│  - Magisk / KernelSU Root Exec │  - Localhost Web Orchestrator          │
├────────────────────────────────┴────────────────────────────────────────┤
│                       Execution Environments                            │
│  1. PRoot Linux (Debian / Alpine with glibc, apt, gcc, python3, git)    │
│  2. Host Android Shell (Bionic libc, Termux shims, native binaries)     │
│  3. Superuser Shell (Magisk `su` for /system, /data/data, APK modding)  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ Key Highlights

### 1. 🧠 Autonomous Agent Loop & Toolchain
- **Multi-Turn Problem Solving**: Plans, writes code, executes commands, reads error logs, self-corrects, and validates output autonomously.
- **Precision File Tools**: `write_file`, `edit_file`, `multi_edit`, and search tools designed to handle full codebases without context blowout.
- **Git Checkpointing**: Automatically commits workspace states before critical changes; supports instant rollback (`revert_changes`).

### 2. 🐧 Linux PRoot & Root Toolchain (Magisk / KernelSU)
- **Built-in Linux System**: Deploys a full Linux rootfs (`/data/data/com.sam.agent/files/rootfs`) with `apt`, `git`, `python3`, and build tools.
- **Direct Superuser Access (`su`)**: When sandbox mode is disabled, SAM can access system partitions (`/system`, `/data/data`, `/data/adb`), modify Android settings, and build/modify APKs natively via `aapt2` and `apksigner`.

### 3. ⌨️ Interactive VT100 Terminal with Auto-Suggestions
- Full ANSI/VT100 terminal integrated into the app.
- **Smart Suggestion Bar**: Detects typed characters in real time and offers instant command autocompletions (`git`, `python3`, `npm`, `pkg`, `su`, etc.) with physical & virtual keyboard navigation.

### 4. 🌐 Automated Localhost & Live App Verification
- **Background Servers**: Launches and tracks web servers (`start_server`) inside dedicated project folders.
- **Auto-Freeing Port Conflicts**: Automatically clears orphaned/leftover ports from old sessions.
- **Deep HTTP Verification (`http_check`)**: Tests HTTP 200 status, resolves CSS/JS/image assets, checks JavaScript syntax via Node, and validates live DOM/API response content.

### 5. 🔑 Multi-Model Pools & Rate-Limit Avoidance
- **Gemini Key Pool (`GEMINI_BUILDER_API_KEY_POOL`)**: Supports comma-separated keys (`key1,key2,key3...`) with automatic rotation when quota limits or rate-limits are reached.
- **Web Search Multi-Provider**: Built-in support for **Tavily**, **Serper**, **Brave Search**, and **DuckDuckGo**.

### 6. 🌍 Multilingual Interface & Auto-Detection
- Automatically adopts the Android system language on startup.
- Full UI and error messaging available in **العربية (Arabic)**, **English**, **Français (French)**, **हिन्दी (Hindi)**, and **Português do Brasil (Portuguese)**.

---

## 🚀 Practical Step-by-Step Guide

### Step 1: Installation & Setup
1. Download [**`SAMAgent.apk`**](https://github.com/gdjjvdth/SAM-Agent/releases/download/v1.0.0/SAMAgent.apk).
2. Install the APK and launch **SAM Agent**.
3. Grant storage and notification permissions. The internal PRoot environment initializes automatically on the first launch.

### Step 2: Configure API Keys
1. Open the drawer menu and tap **Settings (⚙️)**.
2. Under **Model & API Configuration**, input your API keys:
   - **Gemini Key Pool**: `AIzaSyA...1, AIzaSyB...2, AIzaSyC...3` (rotates seamlessly).
   - **Search API Key**: Add your Tavily or Serper API key for real-time web research.
3. Tap **Save**.

### Step 3: Running Real-World Engineering Tasks
Open a new conversation and give SAM instructions:

* **Example 1: Building a Web Application**
  > *"Create a responsive Kanban board web app with drag-and-drop support, dark mode, and local storage. Start the server and verify it."*
  - SAM creates a dedicated workspace, writes HTML/CSS/JS, starts the local server on `http://localhost:8000/`, runs `http_check`, and provides the live link.

* **Example 2: System & Deep Root Inspection (Magisk)**
  > *"Inspect the device's build properties in /system/build.prop and list installed third-party packages using root."*
  - SAM executes `su -c` or `sam root`, reads the system files, and formats a clean report.

* **Example 3: Python Automation & Data Extraction**
  > *"Write a Python script to fetch the latest tech headlines from Hacker News API, save them to a JSON file, and display a formatted table."*

---

## 📱 Hardware & PhoneBridge Features

SAM Agent connects directly to Android hardware capabilities via an internal PhoneBridge:
- 🔦 **Flashlight / Torch**: Toggle device torch for hardware status indication.
- 🔋 **Battery & Thermal Monitoring**: Read current battery level, charging status, and temperature.
- 🔔 **System Notifications & TTS**: Push native status notifications and speech synthesis.
- 📋 **System Clipboard**: Read and write system clipboard data seamlessly.

---

## 📦 Download & Release Information

| Resource | Link |
| :--- | :--- |
| 🚀 **Latest Beta Release** | [GitHub Releases v1.0.0 (Beta)](https://github.com/gdjjvdth/SAM-Agent/releases/tag/v1.0.0) |
| 📥 **Direct APK Download** | [SAMAgent.apk (40 MB)](https://github.com/gdjjvdth/SAM-Agent/releases/download/v1.0.0/SAMAgent.apk) |
| 🏷️ **Version Status** | Public Beta |
| 📜 **License** | MIT License |

---
*Built with ❤️ for autonomous on-device software engineering.*
