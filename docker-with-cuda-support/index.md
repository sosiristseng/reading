# Docker with CUDA support


Setup docker with GPU (CUDA) containers.

<!--more-->

## Ubuntu-based

Setup the deb repository **for the LTS versions**

```bash
# Install docker via the convenience script
curl https://get.docker.com | sh && sudo systemctl --now enable docker

# CUDA runtime support (optional)
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -fsSL "https://nvidia.github.io/nvidia-docker/gpgkey" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/nvidia-docker-keyring.gpg
curl -fsSL "https://nvidia.github.io/nvidia-docker/${distribution}/nvidia-docker.list" | sudo tee /etc/apt/sources.list.d/nvidia-docker.list > /dev/null
sudo apt update && sudo apt install nvidia-container-toolkit
sudo systemctl restart docker
```

## Arch-based

install docker and [activate](https://wiki.archlinux.org/title/Docker) it.


```bash
sudo pacman -S docker
sudo systemctl enable --now docker.service

# CUDA runtime support
paru -S nvidia-container-toolkit
sudo systemctl restart docker
```

## Test your installation

```bash
sudo docker docker run hello-world

sudo docker run --gpus all nvidia/cuda:11.0-base nvidia-smi
```

## See also

- [CUDA container toolkit install guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)
- [Medium post about installing nvidia-container-toolkit (Traditional Chinese)](https://grady1006.medium.com/ubuntu18-04%E5%AE%89%E8%A3%9Ddocker%E5%92%8Cnvidia-docker-%E4%BD%BF%E7%94%A8%E5%A4%96%E6%8E%A5%E9%A1%AF%E5%8D%A1-1e3c404c517d)

