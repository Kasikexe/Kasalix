# Features Overview

Kasalix AI Chat is a self-hosted local AI platform with a rich set of features for both individuals and teams.

## Core Features

### 💬 AI Chat

Full-featured chat interface with streaming responses:

- **Real-time streaming** — See responses as they're generated
- **Multiple models** — Switch between any Ollama model
- **Conversation history** — All chats saved automatically
- **Rich formatting** — Markdown, code blocks, tables
- **Image upload** — Share images with vision-capable models

### 🛠️ Agent Mode

AI agents with tool access for autonomous task execution:

- **Calculator** — Complex mathematical expressions
- **Web Search** — Internet search capabilities
- **Code Execution** — Run code in sandboxed environment
- **Image Generation** — Create images from text
- **File Operations** — Read/write files in workspace
- **Data Processing** — JSON, text, color, hash tools
- **Unit Conversion** — Convert between measurement units
- **Random Generation** — Generate passwords, numbers, IDs

### 🎬 Video Editor Mode

AI-powered video editing assistance:

- **Scene analysis** — AI understands video structure and content
- **Script generation** — Create and refine video scripts
- **Edit suggestions** — Get intelligent recommendations for cuts and transitions
- **Metadata extraction** — Pull technical details from video files
- **Voiceover scripts** — Generate narration text from video content
- **Batch processing** — Handle multiple video files at once

## Platform Features

### 🌐 Web Interface

Modern, responsive web UI accessible from any browser:

- **Dark/Light themes** — Eye-friendly design
- **Mobile responsive** — Works on phones and tablets
- **Touch support** — Native touch interactions
- **Fast loading** — Optimized with Vite build

### 🖥️ Server GUI

Desktop application for server management:

- **Real-time monitoring** — CPU, RAM, GPU usage
- **Server control** — Start/stop with one click
- **Network info** — All local IPs displayed
- **Model viewer** — See loaded models
- **Client downloads** — Download EXE/APK from within the app
- **Startup checks** — Automatic dependency verification

### 📱 Multi-Device Support

Use Kasalix from any device on your network:

- **Windows Desktop** — Full-featured Electron app
- **Android** — Capacitor mobile app
- **Any browser** — No installation needed for basic use
- **Multiple concurrent users** — Each with their own account

## Security Features

### 🔐 Authentication

- **Password-based** — Username + password login
- **Argon2 hashing** — Industry-standard password security
- **Session tokens** — UUID-based, 24-hour TTL
- **Rate limiting** — Protects against brute force attacks

### 🔒 Encryption

- **HTTPS support** — Self-signed or custom certificates
- **Auto-generated certs** — HTTPS ready out of the box
- **HTTP fallback** — For trusted local networks

### 🛡️ Input Validation

- **Path traversal protection** — Prevents directory escape attacks
- **Command injection prevention** — Sanitizes terminal commands
- **File type validation** — Restricts upload types

## Deployment Features

### 📦 Easy Installation

- **NSIS installer** — Standard Windows setup experience
- **Auto-dependency check** — Bun, Ollama verified on startup
- **Self-contained** — Everything in one directory
- **Zero cloud dependency** — Works completely offline

### 🔄 Auto-Update

- **Windows client** — Automatic updates from server
- **Download manager** — Pull releases from GitHub
- **Server-side updates** — Download new installer from GitHub

### 🎨 Customization

- **Multiple models** — Choose any Ollama model
- **Configurable settings** — Theme, temperature, context length
- **Modelfiles** — Create custom model configurations
- **Environment variables** — Flexible server configuration

## Infrastructure

### ⚡ Performance

- **Bun runtime** — Fast JavaScript execution
- **Hono framework** — Lightweight HTTP handling
- **Streaming responses** — Low latency AI interactions
- **GPU acceleration** — NVIDIA GPU support via Ollama

### 📊 Monitoring

- **Real-time stats** — CPU, RAM, GPU in dashboard
- **Server logs** — Captured and displayed
- **Model status** — See what's loaded in memory
- **Network info** — All accessible IPs shown

### 🔧 Developer Tools

- **REST API** — Full API for custom integrations
- **Tool system** — Extensible tool architecture
- **Terminal access** — Execute commands from browser
- **File workspace** — Persistent file storage

## Comparison

| Feature | Kasalix | ChatGPT | Ollama WebUI |
|---------|---------|---------|-------------|
| Fully local | ✅ | ❌ | ✅ |
| Multi-device | ✅ | ✅ | ✅ |
| No registration required | ✅ | ❌ | ✅ |
| Server monitoring | ✅ | ❌ | ❌ |
| Agent mode | ✅ | ✅ | ❌ |
| Video Editor Mode | ✅ | ❌ | ❌ |
| Windows client | ✅ | ✅ | ❌ |
| Android client | ✅ | ✅ | ❌ |
| Auto-update | ✅ | ✅ | ❌ |
| GPU monitoring | ✅ | ❌ | ❌ |
| HTTPS support | ✅ | ✅ | ❌ |
| File upload | ✅ | ✅ | ✅ |
| Image generation | ✅ | ✅ | ❌ |
| Free & open source | ✅ | ❌ | ✅ |

## Roadmap

Planned features for future releases:

- 🐳 Docker support
- 📚 RAG (Retrieval Augmented Generation)
- 🌐 Custom knowledge bases
- 📊 Usage analytics dashboard
- 🔌 Plugin system
- 🤖 Custom agent workflows
- 🎤 Voice input/output
- 📱 iOS client
- 🔄 WebSocket API

