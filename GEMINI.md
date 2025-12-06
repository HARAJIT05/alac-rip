# GEMINI.md

## Project Overview

This project, **alac-rip**, is a web-based user interface for downloading high-quality audio from Apple Music. It serves as a friendly frontend to underlying command-line tools, orchestrating the authentication and download processes.

The system is composed of three main parts:
1.  **Web UI (Python/Flask):** The user interface for searching, configuring, and initiating downloads. It manages the backend processes.
2.  **Apple Music Downloader (Go):** The core tool that fetches tracks, handles metadata, and saves files. (Found in `amd_check/` or cloned as `apple-music-downloader`).
3.  **Wrapper (C++):** A critical component that handles decryption and authentication with Apple Music's servers. It emulates an Android environment to interact with Apple's libraries.

## Directory Structure

*   `main.py`: The master setup and entry script. It handles environment provisioning, compilation of dependencies, and starting the web server.
*   `shell.nix`: Configuration for the Nix package manager to create a reproducible development environment with all necessary tools (Go, Python, ffmpeg, etc.).
*   `app/`: The Flask web application source code.
    *   `routes.py`: Main logic for handling requests and managing subprocesses (wrapper and downloader).
    *   `templates/`: HTML files for the UI.
*   `amd_check/`: Source code for the Go-based Apple Music downloader.
*   `wrapper_temp/` & `wrapper/`: Directories used during the build process of the C++ wrapper.

## Building and Running

The project is designed to be self-bootstrapping via the `main.py` script.

### Prerequisites
*   **Linux** (x86_64 or aarch64).
*   **Root privileges** (for initial Nix installation and setup).

### Start Command
To set up and run the application, execute:

```bash
sudo python3 main.py
```

**What this does:**
1.  Checks for/installs the **Nix package manager**.
2.  Enters a **Nix shell** defined in `shell.nix`.
3.  Downloads the **Android NDK (r23b)** if missing (required for the wrapper).
4.  Clones and compiles the **C++ Wrapper** using CMake and the NDK.
5.  Clones the **Apple Music Downloader** (Go).
6.  Starts the **Flask Web Server** on port `5000`.

### Accessing the UI
Once running, open your browser to:
`http://localhost:5000`

## Development Conventions

*   **Subprocesses:** The Python backend controls the Go downloader and C++ wrapper via `subprocess.Popen`. Interaction happens through standard input/output streams.
*   **Authentication:** The `wrapper` runs as a persistent process. The web UI sends login credentials to it, and it maintains the session.
*   **Compilation:** The wrapper is a C++ project that *must* be cross-compiled for Android (using the NDK) because it loads Android-specific libraries (`.so` files) to handle decryption. The `main.py` script handles this complex build process.
*   **Configuration:** Downloader settings are typically managed via `config.yaml` in the downloader's directory, which the Web UI exposes for editing.

## Troubleshooting Notes

*   **Wrapper Build:** If the wrapper fails to build, ensure the Android NDK is correctly downloaded to `deps/` and that `cmake` and `make` are available (added to `shell.nix`).
*   **Nix:** If `nix-shell` is not found after installation, you may need to restart your terminal or source the nix profile.
