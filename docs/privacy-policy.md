# Privacy Policy

**Last updated: July 2026**

## Introduction

Kasalix AI Chat ("the Software") is a self-hosted local AI platform designed to run on your own hardware. This Privacy Policy explains how the Software handles data when you use it.

## 1. Data Collection

### What We Collect

**The Software itself does not collect any data.** Because Kasalix is self-hosted and runs entirely on your local machine or network, no data is transmitted to external servers operated by us.

The following data is stored locally on your server:

| Data Type | Where It's Stored | Purpose |
|-----------|-------------------|---------|
| Chat messages | Local filesystem | Conversation history |
| User accounts | Local filesystem | Authentication |
| Uploaded files | Local filesystem | File sharing with AI |
| Generated images | Local filesystem | Image output |
| Settings/preferences | Local filesystem | User configuration |
| Session tokens | In-memory | Active session management |

### What We Do NOT Collect

- **No telemetry** — The Software does not track usage statistics
- **No analytics** — No analytics services are embedded
- **No crash reports** — Error data stays on your machine
- **No personal information** — We don't collect names, emails, or contact details
- **No IP logging** — Server logs don't record IP addresses of users (except for rate-limiting purposes, which are in-memory only)

## 2. Data Storage

### Local Storage

All data is stored locally on the server machine in the installation directory. Data is stored as:
- **JSON files** for conversations and settings
- **Binary files** for uploaded images and generated content
- **In-memory** for active sessions (lost on server restart)

### Data Retention

Data is retained until you choose to delete it:
- **Conversations**: Deleted when you delete them in the UI
- **Accounts**: Persist until the user database is deleted
- **Uploaded files**: Persist until manually removed
- **Session tokens**: Expire after 24 hours (configurable)

## 3. Data Sharing

### Third-Party Services

The Software may communicate with the following services only when explicitly configured:

| Service | Purpose | When |
|---------|---------|------|
| **GitHub** | Download client updates | When you click "Download" in the Server GUI |
| **Ollama** | AI model inference | Local network only (port 11434) |

### No Data Sale

We do not sell, trade, or transfer any data to third parties. The Software has no mechanism to do so.

## 4. Security

### Local Security

Since the Software runs on your hardware, security is your responsibility:

- **Network access**: The server is bound to your local network
- **Authentication**: Passwords are hashed with Argon2
- **Encryption**: HTTPS is enabled by default
- **Firewall**: Port 3001 must be opened for LAN access

### Password Storage

Passwords are:
- Hashed using **Argon2** (or bcrypt as fallback)
- Automatically salted
- Never stored in plain text
- Never logged or exposed

## 5. User Rights

Since all data is stored locally on your server, you have full control:

- **Access**: View all stored data in the application
- **Deletion**: Delete conversations, files, and account data through the UI
- **Portability**: Data is stored in standard formats (JSON, images)
- **Correction**: Edit your username and settings

## 6. Children's Privacy

The Software is not specifically directed at children under 13. However, since the Software is self-hosted and does not collect any data externally, this is not applicable in the traditional sense.

## 7. Changes to This Policy

If this policy is updated, the "Last updated" date at the top will change. Since the Software is self-hosted, updates are delivered through the normal update process.

## 8. Contact

For questions about this privacy policy, please open an issue on the [GitHub repository](https://github.com/Kasikexe/Kasalix).

## 9. Self-Hosted Nature

**Important:** Because Kasalix is self-hosted:
- The software authors have no access to your data
- Data never leaves your network unless you configure it to
- You are responsible for the security of your own server
- Network traffic between clients and server is your responsibility
