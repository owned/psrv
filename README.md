# PSRV Stream Server 🎥

**A powerful, portable streaming server for OBS with zero-config external access.**

PSRV (Portable Streaming Runtime Video) allows you to stream from OBS Studio to a custom, password-protected website that you can share with friends anywhere in the world. It combines the power of an RTMP server, HLS transcoding, and WebRTC low-latency delivery into a single, easy-to-use application.

![PSRV Interface](https://via.placeholder.com/800x450?text=PSRV+Stream+Server+Interface)

## ✨ Key Features

- **🚀 Truly Portable**: Runs as a single `.exe` file. No Node.js or complex installation required.
- **🔐 Secure & Private**: Password-protected viewer with built-in Cloudflare Tunnel support for secure external access.
- **⚡ Ultra-Low Latency**: Supports **WebRTC (WHIP/WHEP)** for sub-second delay streaming.
- **📱 Universal Compatibility**: Falls back to **HLS** for perfect playback on mobile devices (iOS/Android).
- **🔄 Auto-Updates**: Automatically checks for and installs new features and fixes.
- **🎛️ Advanced Control Panel**:
    - Real-time Bitrate & Viewer Stats
    - Health Check Dashboard
    - Hot-swappable Stream Sources
    - Dark/Light Theme
    - System Tray Integration

## 🚀 Quick Start

### 1. Download & Run
Download the latest `PSRV-StreamServer-Setup.exe` from the [Releases](https://github.com/owned/psrv/releases) page and install it.

### 2. Configure OBS Studio
1.  Open **OBS Studio**.
2.  Go to **Settings > Stream**.
3.  Set **Service** to `Custom`.
4.  **Server**: `rtmp://localhost:1935/live`
5.  **Stream Key**: `stream` (default)
6.  Click **Apply**.

### 3. Start Streaming
1.  In PSRV, click **START ALL SERVICES**.
2.  In OBS, click **Start Streaming**.
3.  Your stream is now live locally at `http://localhost:8080`!

## 🌐 External Access (Share with Friends)

You don't need to port forward! PSRV integrates with **Cloudflare Tunnel** for free, secure external access.

1.  In the PSRV Control Panel, scroll to the **Cloudflare Tunnel** card.
2.  Click **Start**.
3.  Wait a moment for the **Public URL** to appear (e.g., `https://random-name.trycloudflare.com`).
4.  Share this link with your friends! They can watch your stream securely from any device.

## 🛠️ Advanced Features

### WebRTC (Low Latency)
For real-time interaction (gaming, chatting), enable WebRTC:
1.  Go to **Advanced Settings**.
2.  Ensure a **TURN Server** is configured (we provide defaults, or use your own).
3.  Viewers will automatically use WebRTC if supported, falling back to HLS if needed.

## 🖥️ Screen Sharing & WebRTC
PSRV includes a powerful **WebRTC** engine designed for ultra-low latency screen sharing and gaming.

### 🌟 Key Features
*   **WHIP/WHEP Protocol**: Industry-standard WebRTC signaling for sub-second latency (< 500ms).
*   **Dual Broadcast Modes**:
    *   **RTMP Relay**: Re-stream your high-production OBS output via WebRTC.
    *   **Direct Capture**: Share your screen, window, or webcam directly from the app (no OBS required).
*   **High Fidelity**: Supports **4K resolution** and bitrates up to **50 Mbps**.
*   **Hot-Swapping**: Instantly switch between "Game Feed" and "Webcam" without disconnecting viewers.
*   **Public Lobby**: Optionally list your room in the public directory for open access.

### ⚙️ Configuration Guide
1.  **Select Source**: In the WebRTC card, choose:
    *   `RTMP Input`: To use your OBS stream.
    *   `Webcam & Microphone`: To capture directly from your device.
2.  **Quality Settings**:
    *   **Latency Mode**: `Ultra-Low` (0.5s) for gaming, `Balanced` for better quality on poor connections.
    *   **Bitrate**: Adjustable in Advanced Settings (default: Unlimited).
3.  **TURN Server**:
    *   Crucial for connecting through firewalls/NATs.
    *   Enter your credentials in **Advanced Settings > WebRTC**.
    *   *Recommendation*: Get a free account at [metered.ca](https://www.metered.ca).

### 🏥 Health Dashboard
Click the **Running Health Checks** button (heartbeat icon) to see the status of all subsystems:
- HTTP/RTMP Server connectivity
- WebSocket (Chat/Stats) latency
- Cloudflare Tunnel status
- WebRTC TURN server reachability

## ⚙️ Configuration

All settings can be changed directly in the app:
- **Stream Title**: Change the title displayed on the viewer page.
- **Password**: Protect your stream (default: `stream123`).
- **Ports**: Customize HTTP (8080) and RTMP (1935) ports.
- **Auto-Start**: Configure PSRV to launch on system startup or start services automatically.

## 🤝 Troubleshooting

**"Stream is offline"**
- Ensure OBS is actually streaming.
- Check that the **Stream Key** in OBS matches the one in PSRV.

**"High Latency"**
- Switch to **WebRTC** mode if possible.
- In OBS, check your Output settings. Ensure **Keyframe Interval** is set to **2s** or **1s** for lower latency HLS.

**"Update Failed"**
- Ensure you have an internet connection.
- Download the latest version manually from GitHub if the auto-updater persists in failing.

## 📝 License

**Proprietary Software.**
All rights reserved. Unauthorized copying, modification, distribution, or use of this software is strictly prohibited.
