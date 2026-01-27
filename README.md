# TensorFlow GPU Development Environment

A ready-to-use TensorFlow environment with NVIDIA GPU support for VS Code.

## What's Included

| Category | Versions |
|----------|----------|
| **GPU** | CUDA 12.5, cuDNN 9.1 |
| **ML** | TensorFlow 2.16, Keras 3.3, Scikit-learn 1.4 |
| **Python** | Python 3.10, NumPy 1.24, Pandas 2.2, Matplotlib 3.10 |
| **Tools** | JupyterLab, TensorBoard (auto-starts on port 6006) |

Based on [NVIDIA's TensorFlow 24.06 container](https://docs.nvidia.com/deeplearning/frameworks/tensorflow-release-notes/rel-24-06.html).

> **No NVIDIA GPU?** Use the CPU version instead: [gperdrizet/tensorflow-CPU](https://github.com/gperdrizet/tensorflow-CPU)

---

## Requirements

- **NVIDIA GPU** (Pascal or newer) with driver ≥545
- **Docker** with GPU support ([Windows](https://docs.docker.com/desktop/setup/install/windows-install) | [Linux](https://docs.docker.com/desktop/setup/install/linux))
- **VS Code** with the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

> **Linux users:** Also install the [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

---

## Quick Start

1. **Fork** this repository (click "Fork" button above)

2. **Clone** your fork:
   ```bash
   git clone https://github.com/<your-username>/tensorflow-GPU.git
   ```

3. **Open in VS Code:**
   ```bash
   cd tensorflow-GPU
   code .
   ```

4. **Reopen in Container** when prompted (or press `F1` → "Dev Containers: Reopen in Container")

5. **Verify** by running `notebooks/environment_test.ipynb`

---

## TensorBoard

TensorBoard starts automatically and is available at **http://localhost:6006**

```bash
# Attach to TensorBoard session
screen -r tensorboard

# Detach without stopping
Ctrl+A, D
```

Place your logs in the `logs/` directory.

---

## Keeping Your Fork Updated

```bash
# Add upstream (once)
git remote add upstream https://github.com/gperdrizet/tensorflow-GPU.git

# Sync
git fetch upstream
git merge upstream/main
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Docker won't start | Enable virtualization in BIOS |
| Permission denied (Linux) | Add user to docker group, then log out/in |
| GPU not detected | Update NVIDIA drivers (≥545) |
| Container build fails | Check internet connection |

