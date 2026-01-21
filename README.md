# Containerized Tensorflow GPU development environment

A containerized TensorFlow AI/ML development environment with NVIDIA GPU support. This repository provides a consistent development environment using VS Code Dev Containers, eliminating the need for manual environment setup.

The underlying docker container is based on NVIDIA's TensorFlow 24.06 container. For details see:

- George's TensorFlow 2.16 container on DockerHub: [gperdrizet/tensorflow-gpu](https://hub.docker.com/r/gperdrizet/tensorflow-gpu)
- NVIDIA's [TensorFlow Release 24.06](https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel-24-06.html)

The container needs Docker and a compatible NVIDIA driver installed. It should support GPUs back to Pascal on both Windows and Linux (MacOS users should be able to run it without GPU support - see below). 

## Prerequisites

Before you can use this development container, you need to install:

1. **NVIDIA driver >=545** (slightly older drivers may work - try it before you make major changes to your host system)
2. **Docker** (see platform-specific instructions below)
2. **Visual Studio Code** - [Download here](https://code.visualstudio.com)
3. **Dev Containers extension** - Install from the VS Code Extensions marketplace (`ms-vscode-remote.remote-containers`)

---

## Docker installation instructions

### Windows

Full installation documentation here: [Install Docker Desktop on Windows](https://docs.docker.com/desktop/setup/install/windows-install)

1. **Check system requirements**
   - Windows 10 64-bit: Pro, Enterprise, or Education (Build 19041 or higher), or Windows 11
   - Windows 11 64-bit: Enterprise, Pro, or Education version 23H2 (build 22631) or higher
   - WSL 2.1.5 or later
   - 64-bit processor with Second Level Address Translation (SLAT)
   - 4GB system RAM
   - Enable hardware virtualization in BIOS/UEFI. For more information, see Virtualization.

2. **Install or update WSL**

    Full documentation here: [WSL: Verification and setup](https://docs.docker.com/desktop/setup/install/windows-install#wsl-verification-and-setup)

    - To check your WSL version, open PowerShell as Administrator and run:

    ```powershell
    wsl --version
    ```

    - Then install or update as needed:

    ```powershell
    wsl --install
    ```

    ```powershell
    wsl --update
    ```
   - Restart your computer when prompted

3. **Download and install Docker Desktop**
   - Download Docker Desktop from [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
   - Run the installer and follow the prompts
   - Ensure "Use WSL 2 instead of Hyper-V" is selected during installation

4. **Start Docker Desktop**
   - Launch Docker Desktop from the Start menu
   - Wait for Docker to fully start (the whale icon in the system tray will stop animating)

5. **Verify installation**
   - Open a terminal (PowerShell or Command Prompt) and run:
     ```powershell
     docker --version
     ```

    The command should complete without error.

> **Note for GPU support:** To use GPU acceleration on Windows, you'll need an NVIDIA GPU with updated drivers.

---

### Linux

For Linux set-up instructions, refer to [Install Docker Desktop on Linux](https://docs.docker.com/desktop/setup/install/linux).

> **Note for GPU support:** To use GPU acceleration on Windows, you'll need an NVIDIA GPU with updated drivers and the [NVIDIA container toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).

### macOS

Apple dropped NVIDIA support around 2014, but you can still use this container to run TensorFlow on CPU only. See full docker setup documentation here: [Install Docker Desktop on Mac](https://docs.docker.com/desktop/setup/install/mac-install)

1. **Check system requirements**
   - macOS 14 (Sonoma) or newer
   - At least 4 GB of RAM

2. **Download Docker Desktop**
   - Download the appropriate version:
     - **Apple Silicon (M1/M2/M3):** Download "Docker Desktop for Mac with Apple silicon"
     - **Intel Mac:** Download "Docker Desktop for Mac with Intel chip"

3. **Install Docker Desktop**
   - Open the downloaded `.dmg` file
   - Drag the Docker icon to the Applications folder
   - Launch Docker from the Applications folder
   - Select 'Use recommended settings'
   - Grant any permissions requested during first launch

4. **Start Docker Desktop**
   - Click the Docker icon in the Applications folder
   - Wait for Docker to fully start (check the whale icon in the menu bar)

5. **Verify installation**
   - Open Terminal and run:
     ```bash
     docker --version
     ```

    The command should complete without error.

> **Note:** macOS does not support NVIDIA GPU passthrough. TensorFlow will run in CPU mode on Mac.

---

## Getting started

1. **Fork this repository** to create your own copy:
   - Click the **"Fork"** button in the top-right corner of this repository's GitHub page
   - Select your GitHub account as the destination
   - This creates your own copy where you can save your work and push changes

2. **Clone your forked repository:**
   ```bash
   git clone https://github.com/<your-username>/tensorflow-GPU.git
   cd tensorflow-GPU
   ```
   > Replace `<your-username>` with your GitHub username

3. **Open the folder in VS Code:**
   ```bash
   code .
   ```

4. **Launch the dev container:**
   - When prompted, click **"Reopen in Container"**
   - Or press `F1` → Type "Dev Containers: Reopen in Container" → Press Enter

5. **Wait for the container to build** (this may take a few minutes on first run)

6. **Start coding!** Open and run `notebooks/test.ipynb` to verify your environment is working.

### Keeping Your Fork Updated

To sync your fork with the latest changes from the original repository:

```bash
# Add the original repo as an upstream remote (only needed once)
git remote add upstream https://github.com/gperdrizet/tensorflow-GPU.git

# Fetch and merge updates
git fetch upstream
git merge upstream/main
```

---

## Troubleshooting

- **Docker not starting:** Ensure virtualization is enabled in your BIOS settings
- **Permission denied errors on Linux:** Make sure you've added your user to the docker group and logged out/in
- **GPU not detected:** Verify NVIDIA drivers and Container Toolkit are properly installed
- **Container build fails:** Ensure you have a stable internet connection for downloading the TensorFlow image