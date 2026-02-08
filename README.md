# OBS Stream Server 🎥

A simple, password-protected streaming server that allows you to stream your OBS gameplay to a custom website accessible both locally and externally via Cloudflare Tunnel.

## ✨ Features

- 🔐 **Password Protection** - Secure your stream with a simple password
- 🌐 **Local & External Access** - Share with friends outside your network
- 🎮 **OBS Integration** - Easy RTMP streaming setup
- 📱 **Responsive Design** - Works on desktop and mobile
- 🚀 **Portable .exe** - Run anywhere without Node.js installation
- ⚡ **Low Latency** - HLS streaming with ~2-5 second delay

## 📋 Prerequisites

**For Development:**
- Node.js 16+ ([Download here](https://nodejs.org/))
- OBS Studio ([Download here](https://obsproject.com/))

**For Portable .exe:**
- OBS Studio only (no Node.js needed!)

## 🚀 Quick Start

### Option 1: Use the Launcher (Easiest!)

**Just double-click `start-server.bat`!**

This automatically:
- Starts the streaming server
- Offers optional Cloudflare Tunnel for external access

All services will open in Windows Terminal tabs (or separate windows if WT not installed).

### Option 2: Run Manually

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Start the server:**
   ```bash
   npm start
   ```

3. **Access the stream:**
   - Local: `http://localhost:8080`
   - For external access, see [CLOUDFLARE_TUNNEL.md](CLOUDFLARE_TUNNEL.md)

### Option 2: Use Portable Executable

**For running on computers without Node.js:**

1. **Build the executable:**
   ```bash
   npm run build
   ```

2. **Copy to target computer:**
   - `obs-stream-server.exe`
   - `start-server.bat`
   - `public/` folder
   - `media/` folder

3. **Run:**
   - Double-click `start-server.bat`
   - Follow prompts for stream settings

See [PORTABLE_GUIDE.md](PORTABLE_GUIDE.md) for detailed instructions.

## 🎮 OBS Configuration

1. Open OBS Studio
2. Go to **Settings** → **Stream**
3. Select **Custom** as Service
4. Configure:
   - **Server:** `rtmp://localhost:1935/live`
   - **Stream Key:** `stream`
5. Click **OK** and start streaming!

## 🔑 Default Password

**Default password:** `stream123`

To change the password, edit `public/app.js`:

```javascript
const CORRECT_PASSWORD = 'your-new-password';
```

## 🌐 Sharing with Friends

### Using Cloudflare Tunnel (Recommended)

Cloudflare Tunnel provides free, unlimited bandwidth for external access.

**Setup:**

1. Install Cloudflare Tunnel:
   ```bash
   winget install --id Cloudflare.cloudflared
   ```

2. Run `start-server.bat` and select Cloudflare Tunnel when prompted

3. Share the generated URL with friends!

See [CLOUDFLARE_TUNNEL.md](CLOUDFLARE_TUNNEL.md) for detailed instructions.

### Using Port Forwarding (Manual)

If you prefer not to use Cloudflare Tunnel:

1. Forward port 8080 on your router
2. Share your public IP: `http://YOUR_PUBLIC_IP:8080`

## 📁 Project Structure

```
PSRV/
├── server.js           # Main server (RTMP + Express)
├── package.json        # Dependencies and scripts
├── public/
│   ├── index.html     # Web interface
│   ├── style.css      # Styling
│   └── app.js         # Client-side logic
└── README.md
```

## 🛠️ Troubleshooting

### Stream not showing?

1. **Check OBS is streaming:**
   - Make sure you've clicked "Start Streaming" in OBS
   - Verify the RTMP settings match: `rtmp://localhost:1935/live`

2. **Wait a few seconds:**
   - Stream takes 5-10 seconds to start after OBS begins

3. **Check console output:**
   - Look for "Stream started: /live/stream" message

### External access not working?

1. **Cloudflare Tunnel:** See [CLOUDFLARE_TUNNEL.md](CLOUDFLARE_TUNNEL.md) for setup

2. **Alternative:** Use port forwarding instead (see above)

3. **Local access only:** External access is optional - you can always use `http://localhost:8080`

### Port already in use?

- Change ports in `server.js`:
  ```javascript
  const HTTP_PORT = 8080; // Change to 8081, 3000, etc.
  ```

## 🎯 Tips

- **Lower stream delay:** Reduce OBS encoder settings (use faster preset)
- **Better quality:** Increase bitrate in OBS settings
- **Mobile viewing:** The interface is fully responsive
- **Session persistence:** Password is remembered during browser session

## 📝 License

MIT License - Feel free to use and modify!

## 🤝 Support

Having issues? Check:
1. OBS streaming settings are correct
2. Server console for error messages
3. Browser console (F12) for client-side errors

---

**Made with ❤️ for streamers**
