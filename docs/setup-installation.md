# Setup & Installation

This guide covers setting up Kasalix AI Chat from start to finish.

## System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| **OS** | Windows 10 (64-bit) | Windows 11 |
| **CPU** | 4 cores, AVX2 support | 8+ cores |
| **RAM** | 8 GB | 16 GB+ |
| **Storage** | 5 GB free | 20 GB+ (for models) |
| **GPU** | GPU with 4GB VRAM | NVIDIA GPU, 6GB+ VRAM |
| **Runtime** | Bun 1.x, Ollama latest | — |

AMD GPUs werent tested

## Installer

### Download

Get the latest setup from [GitHub Releases](https://github.com/Kasikexe/Kasalix/releases):
- Download `Kasalix-AI-Chat-Server-Setup-{version}.exe`

### Run the Installer

1. Double-click the installer
2. Follow the on-screen instructions
3. Choose installation directory (default: `C:\Program Files\AI Chat Server`)
4. Wait for the setup to complete

The server will be available at `http://localhost:3001`.

## Quick Start

### Step 1: Install Ollama

Download and install Ollama from [ollama.com](https://ollama.com). Verify it's running:

```bash
ollama --version
```

### Step 2: Pull a Model

```bash
ollama pull llama3.2    # Small, fast (~2 GB)
ollama pull mistral     # Better results (~4 GB)
```

### Step 3: Start the Server

**Using Server GUI (recommended):** Launch **Kasalix AI Chat Server** from your desktop.

### Step 4: Connect

- **Browser**: Open `http://[SERVER_IP]:3001`
- **Windows App**: Download from the Server GUI → Downloads card
- **Android App**: Download the APK from the server

## Updating

Download the latest installer from GitHub Releases and run it. Your data is preserved.

## Uninstallation

- Windows Settings → Apps → Kasalix AI Chat Server → Uninstall
