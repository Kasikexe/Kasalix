# Setup & Installation

This guide covers setting up Kasalix AI Chat from start to finish.

## System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| **OS** | Windows 10 (64-bit) | Windows 11 |
| **CPU** | 4 cores, AVX2 support | 8+ cores |
| **RAM** | 8 GB | 16 GB+ |
| **Storage** | 5 GB free | 20 GB+ (for models) |
| **GPU** | Not required | NVIDIA GPU, 6GB+ VRAM |
| **Runtime** | Bun 1.x, Ollama latest | — |

## Method 1: Installer (Recommended)

### Download

Get the latest setup from [GitHub Releases](https://github.com/Kasikexe/Kasalix/releases):
- Download `Kasalix-AI-Chat-Server-Setup-{version}.exe`

### Run the Installer

1. Double-click the installer
2. Follow the on-screen instructions
3. Choose installation directory (default: `C:\Program Files\AI Chat Server`)
4. Wait for the setup to complete

### What Gets Installed

```
C:\Program Files\AI Chat Server\
├── backend/              # Bun/Hono server
├── frontend/dist/        # Pre-built web UI
├── server-gui/           # Electron dashboard
├── certs/                # SSL certificates
├── release/              # Client download files
├── run-server.bat        # CLI launcher
└── uninstall.exe
```

## Method 2: Manual / From Source

### Prerequisites

| Tool | Install Command |
|------|----------------|
| **Bun** | `powershell -c "irm bun.sh/install.ps1 | iex"` |
| **Ollama** | Download from [ollama.com](https://ollama.com) |
| **Git** | `winget install Git.Git` |

### Clone and Build

```bash
git clone https://github.com/Kasikexe/Kasalix.git
cd Kasalix
cd backend && bun install
cd ../frontend && npm install && npm run build
cd ..
```

### Run

```bash
cd backend
bun run src/index.ts           # HTTPS (default)
bun run src/index.ts --http    # HTTP mode
```

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

**Command line:** Run `run-server.bat` from the installation directory.

### Step 4: Connect

- **Browser**: Open `http://localhost:3001` or `http://[SERVER_IP]:3001`
- **Windows App**: Download from the Server GUI → Downloads card
- **Android App**: Download the APK from the server

## Updating

Download the latest installer from GitHub Releases and run it. Your data is preserved.

## Uninstallation

- Windows Settings → Apps → Kasalix AI Chat Server → Uninstall
- Or run `uninstall.exe` from the installation directory
