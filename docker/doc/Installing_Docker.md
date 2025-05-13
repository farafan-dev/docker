# 🚀 Installing Docker on Windows and Linux (Ubuntu)

This guide will help you install Docker on both **Windows** and **Ubuntu Linux** step-by-step.

---

## 🪟 Installing Docker on Windows

### ✅ Requirements

- Windows 10/11 (64-bit) Pro, Enterprise, or Education **with WSL2**
- Docker Desktop for Windows

### 🔧 Steps

1. **Install WSL 2**
    - Open PowerShell as Administrator and run:
      ```powershell
      wsl --install
      ```
    - Restart your computer if prompted.

2. **Download Docker Desktop**
    - [Download Docker Desktop](https://www.docker.com/products/docker-desktop)

3. **Install Docker Desktop**
    - Run the installer and follow the instructions.
    - Make sure to **enable WSL 2 integration** during installation.

4. **Run Docker Desktop**
    - After installation, launch Docker Desktop.
    - Wait until the Docker icon in the system tray shows “Docker is running”.

5. **Test Installation**
   Open a terminal or PowerShell and run:
   ```bash
   docker --version
   docker run hello-world


🐧 Installing Docker on Ubuntu (Linux)
✅ Requirements

    Ubuntu 20.04 or later

    sudo privileges

🔧 Steps

    Update packages

sudo apt update
sudo apt upgrade

Install required dependencies

sudo apt install \
ca-certificates \
curl \
gnupg \
lsb-release

Add Docker’s official GPG key

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

Set up the Docker repository

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Install Docker Engine

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

Verify Docker installation

sudo docker --version
sudo docker run hello-world

(Optional) Add current user to docker group to run without sudo:

    sudo usermod -aG docker $USER
    newgrp docker

✅ Verification (on both OS)

Run:

docker run hello-world

You should see a message:

    "Hello from Docker!"

🧠 Notes

    On Windows, Docker Desktop uses WSL2 or Hyper-V under the hood.

    On Linux, Docker runs natively with no virtualization required.

    Use docker version and docker info to check details of your setup.

