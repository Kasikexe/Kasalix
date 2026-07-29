# Network Access

Kasalix is designed to work over your **local area network (LAN)**, allowing multiple devices to connect to the AI server from anywhere in your home or office.

## How It Works

The server binds to `0.0.0.0` by default, meaning it's accessible on all network interfaces. The Server GUI detects and displays your local IP addresses automatically.

```
┌──────────────────────────────────┐
│         Server Machine           │
│  IP: 192.168.1.5                 │
│  Port: 3001                      │
│                                  │
│  ┌────────────────────────────┐  │
│  │  Kasalix Server            │  │
│  │  http://0.0.0.0:3001       │  │
│  └────────────────────────────┘  │
└──────────────────────────────────┘
         │              │
         ▼              ▼
┌──────────────┐  ┌──────────────┐
│  Laptop      │  │  Phone       │
│  http://     │  │  http://     │
│  192.168.1.5 │  │  192.168.1.5 │
│  :3001       │  │  :3001       │
└──────────────┘  └──────────────┘
```

## Finding the Server IP

### Via Server GUI

The **Network Access** card in the Server GUI dashboard shows all detected IP addresses. Look for entries like:
- `192.168.x.x` — Common home network
- `10.x.x.x` — Corporate/enterprise networks
- `172.x.x.x` — Other private networks

### Via Command Line

```bash
ipconfig
```

Look for the **IPv4 Address** under your active network adapter.

### Via the Web UI

Open `http://localhost:3001` on the server machine. The server IP is shown in the connection info.

## Connecting from Other Devices

### From a Browser

Open any modern browser and navigate to:
```
http://[SERVER_IP]:3001
```

For example:
```
http://192.168.1.5:3001
```

### From the Windows App

1. Launch the app
2. Enter the server address: `http://192.168.1.5:3001`
3. Create an account or log in

### From the Android App

1. Launch the app
2. Enter the server address: `http://192.168.1.5:3001`
3. Create an account or log in

## Firewall Configuration

For other devices to connect, port 3001 must be open in the server's firewall.

### Windows Firewall

**Automatic (recommended):**
The installer should add a firewall rule automatically.

**Manual:**
```powershell
# Open port 3001 for all profiles
netsh advfirewall firewall add rule name="Kasalix AI Chat" dir=in action=allow protocol=TCP localport=3001

# Or for private networks only (more secure)
netsh advfirewall firewall add rule name="Kasalix AI Chat" dir=in action=allow protocol=TCP localport=3001 profile=private
```

**To remove the rule later:**
```powershell
netsh advfirewall firewall delete rule name="Kasalix AI Chat"
```

### Third-Party Firewalls

If you use a third-party firewall (Norton, McAfee, BitDefender, etc.), add an exception for:
- **Program**: `bun.exe` or the Kasalix server
- **Port**: `3001`
- **Protocol**: TCP

## Sharing the Server Address

### On the Same Network

Simply share the IP address and port displayed in the Server GUI:
```
Server: http://192.168.1.5:3001
```

### Via QR Code

The download page (`http://[SERVER_IP]:3001/download`) can be bookmarked or shared. A QR code feature is planned for a future release.

## HTTPS / SSL

### Default (Self-Signed)

The server uses self-signed certificates by default. When connecting from a browser:
1. You'll see a "Your connection is not private" warning
2. Click **Advanced** → **Proceed to [IP] (unsafe)**
3. This is safe on your local network

### Custom Certificates

For trusted HTTPS, see the [Configuration guide](configuration.md#https-configuration).

### HTTP Mode

Toggle HTTP mode in the Server GUI to disable encryption:
- **Faster** — No SSL overhead
- **Unencrypted** — Only use on trusted networks
- **No warnings** — Browsers connect directly

## Multiple Network Interfaces

If your computer has multiple network adapters (Ethernet, Wi-Fi, VPN, virtual machines), the server is accessible on all of them. The Server GUI shows all detected IPs.

**Common interfaces:**
- **Ethernet**: Usually the fastest, most reliable
- **Wi-Fi**: Convenient, may be slower
- **VPN**: Accessible if connected, but may add latency
- **Virtual adapters**: Docker, VMware, VirtualBox — typically not needed

## Internet Access (Not Recommended)

> ⚠️ **Warning:** Exposing Kasalix to the internet without additional security is **not recommended**. The server is designed for local network use.

If you must access the server remotely, use a **VPN** (WireGuard, Tailscale, ZeroTier, or OpenVPN) instead of port forwarding.

### Tailscale Example

1. Install Tailscale on both server and client devices
2. Both devices appear on the same Tailscale network
3. Connect using the Tailscale IP: `http://100.x.x.x:3001`
4. Traffic is encrypted end-to-end

## Troubleshooting

**Other devices can't connect:**
- Verify the server is running (green indicator in the GUI)
- Check the IP address is correct
- Ensure devices are on the same network
- Check firewall settings on the server
- Try `ping [SERVER_IP]` from the client device
- Try `telnet [SERVER_IP] 3001` or `Test-NetConnection [SERVER_IP] -Port 3001` in PowerShell

**Connection is slow:**
- Use a wired Ethernet connection for the server
- Check Wi-Fi signal strength
- Other devices streaming video can affect performance
- The AI model response time is the main bottleneck, not network speed

**Server shows wrong IP:**
- The Server GUI filters out virtual adapters (Docker, VMware, etc.)
- If your real IP is filtered, check there's no "virtual" in the adapter name
- Use `ipconfig` to find the correct IP manually
