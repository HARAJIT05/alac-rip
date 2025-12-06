# Apple Music Downloader Web UI

A simple web interface for the Apple Music Downloader, making it easier to download your favorite tracks with a user-friendly GUI.

## 🎵 About

This project is a humble web interface wrapper built around the excellent work of other developers in the Apple Music downloading community. It provides a clean, browser-based UI to interact with the powerful Apple Music Downloader tools without needing to use command-line interfaces.

**This project would not exist without the amazing work of:**
- **[zhaarey/apple-music-downloader](https://github.com/zhaarey/apple-music-downloader)** - The core Go-based Apple Music downloader that powers all the downloading functionality
- **[zhaarey/wrapper](https://github.com/zhaarey/wrapper)** - The authentication wrapper that handles Apple Music login and session management

All credit for the actual downloading capabilities goes to these original creators. This UI is simply a convenience layer on top of their excellent tools.

## ✨ Features

- **🌐 Web-based Interface**: Clean, modern web UI accessible from any browser
- **🔐 Auto-Login**: Save credentials for automatic login on startup
- **🎵 Multiple Formats**: Support for ATMOS, AAC, and standard downloads
- **📊 Real-time Logs**: Live streaming of download progress and wrapper status
- **⚙️ Settings Management**: Easy configuration of all downloader options via web interface
- **🎯 Smart Controls**: Intuitive format selection with Special Audio toggle
- **📱 Responsive Design**: Works on desktop and mobile browsers
- **🔄 Auto-retry**: Intelligent handling of failed connections and auto-login

## 🚀 Quick Start

### Prerequisites



- **Linux environment** (this tool is designed for Linux, also works on WSL)

- **Nix Package Manager** (Optional - will be automatically installed if missing)

- **Git** (for cloning the repository)

- **Root access** (only required if Nix needs to be installed)



### Installation



1. **Clone this repository:**

   ```bash

   git clone https://github.com/lalit22km/alac-rip.git

   cd alac-rip

   ```



2. **Run the setup:**

   ```bash

   python3 main.py

   ```

   

   The application will automatically:

   - Check for Nix package manager and install it if missing

   - Enter a reproducible environment with all dependencies (ffmpeg, gpac, python, etc.)

   - Download and compile the wrapper tool

   - Clone the Apple Music Downloader



3. **Access the web interface:**

   - Open your browser and navigate to `http://localhost:5000`

   - The interface will be ready to use!

## 📖 Usage

### First Time Setup

1. **Login**: Click "Login to Wrapper" and enter your Apple Music credentials
2. **Wait for Success**: Watch the wrapper logs until you see `[.] response type 6` 
3. **Configure Settings**: Click the ⚙️ Settings button to customize download preferences
4. **Start Downloading**: Paste Apple Music URLs and choose your format

### Download Options

- **Standard Download**: Uncheck "Special Audio" for basic downloads
- **ATMOS**: Check "Special Audio" and select "ATMOS" for spatial audio
- **AAC**: Check "Special Audio" and select "AAC" for AAC format

### Settings

The settings page allows you to configure:
- Download folders and file naming
- Audio quality and format preferences  
- Cover art and lyrics options
- Advanced downloader parameters

---

The application acts as a bridge between the web interface and the command-line tools, handling:
- Authentication state management
- Process lifecycle management
- Configuration file editing
- Real-time log streaming
- Download queue management


## ⚠️ Disclaimer

This tool is for educational purposes and personal use only. Please respect Apple's Terms of Service and only download content you have the legal right to access. The developers of this UI wrapper are not responsible for any misuse of the underlying downloading tools.

**Security Note:** This tool requires root privileges for initial setup to install system packages and configure tools. Please review the code before running with elevated privileges.

## 🙏 Acknowledgments

**Massive thanks to:**

- **[@zhaarey](https://github.com/zhaarey)** for creating both the [apple-music-downloader](https://github.com/zhaarey/apple-music-downloader) and [wrapper](https://github.com/zhaarey/wrapper) projects that make this possible
- The entire Apple Music downloading community for their research and tools
- All contributors who help improve these tools

---
