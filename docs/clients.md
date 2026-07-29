# Clients

Kasalix provides two client applications that connect to the server over your local network. Each client gives you access to AI chat, Agent Mode, and other features from any device.

## Windows Desktop App

### Downloading

**From the Server GUI:**
1. Open the Server GUI dashboard
2. Go to the **Downloads** card
3. Click **Download Windows App**
4. The EXE downloads from GitHub to the server's `release/` folder

**From the web:** Open `http://[SERVER_IP]:3001/download` on the target Windows machine.

### Connecting

1. Launch the app
2. Enter the server address (e.g., `192.168.1.5:3001`)
3. Create an account or log in
4. Start chatting

### Features

- 💬 **AI Chat** — Full conversation interface with streaming responses
- 🛠️ **Agent Mode** — AI with tool access (calculator, search, code execution)
- 🎬 **Video Editor Mode** — AI-powered video editing assistance
- 🖼️ **Image Upload** — Share images with the AI for analysis
- 🗂️ **Conversations** — History and thread management
- 🎨 **Theme Support** — Light and dark mode
- 🔄 **Auto-Update** — Checks the server's release folder for updates

## Android App

### Downloading

**From the Server GUI:**
1. Open the Server GUI dashboard
2. Click **Download Android App** in the Downloads card
3. The APK downloads from GitHub to the server's `release/` folder

**From the web:** Open `http://[SERVER_IP]:3001/download` on the target Android device.

### Installation

1. Enable **Install from Unknown Sources** in Android settings
2. Open the APK file and follow the prompts
3. Launch the app and enter the server address

## Troubleshooting

**Client can't find the server:**
- Ensure both devices are on the same local network
- Check the server IP is correct (use the IP shown in the Server GUI)
- Verify the server is running (green indicator in the GUI)
- Check firewall settings — port 3001 must be accessible

**Connection refused:**
- The server might be in HTTPS mode but the client is using HTTP
- Try toggling HTTP mode in the Server GUI
- Restart the server after changing the mode

**Slow responses:**
- AI model response time is the main bottleneck
- Network speed usually isn't the issue on LAN
- Try a smaller/faster AI model



