# deploy-on-tx2
[TOC]

## Install os by sdkmanage
### Request 
* [NVIDIA Jetson SDK Manager - JetPack 4.2(youtube)](https://www.youtube.com/watch?v=s1QDsa6SzuQ)
* [sdkmanager_0.9.14-4964_amd64.deb](https://developer.nvidia.com/nvsdk-manager)
* [DeepStream SDK 4.0.1](https://developer.nvidia.com/deepstream-download)

### Support Developer
#### TX2 Share monitor
```shell=
## Installing the VNC Server
$ sudo apt update
$ sudo apt install vino

## Enable the VNC server to start each time you log in
$ sudo ln -s ../vino-server.service \
    /usr/lib/systemd/user/graphical-session.target.wants
    
## Configure the VNC server
$ gsettings set org.gnome.Vino prompt-enabled false
$ gsettings set org.gnome.Vino require-encryption false

## Set a password to access the VNC server & Replace thepassword with your desired password
$ gsettings set org.gnome.Vino authentication-methods "['vnc']"
$ gsettings set org.gnome.Vino vnc-password $(echo -n 'thepassword'|base64)

## Reboot the system so that the settings take effect
$ sudo reboot
```
https://blog.csdn.net/jiangchao3392/article/details/73252291
### TX2 jetson-inference
* [install-with-sdkmanager-drive](https://docs.nvidia.com/sdk-manager/install-with-sdkm-drive/index.html)

* [Explore the JetPack 4.2 Samples on the NVIDIA Jetsons(youtube)](https://www.youtube.com/watch?v=KROP46Wte4Q)
```shell=
$ cd /usr/local/cuda/bin
$ ./cuda-install-samples-10.0.sh ~
$ cd ~/NVIDIA_CUDA-10.0_Samples
$ make -j4
$ cd ~/NVIDIA_CUDA-10.0_Samples/bin/aarch64/linux/release
$ ./oceanFFT
```


* [jetson-inference](https://github.com/dusty-nv/jetson-inference#hello-ai-world)
* [Building the Project from Source](https://github.com/dusty-nv/jetson-inference/blob/master/docs/building-repo-2.md) 
```shell=
$ cd ~
$ git clone https://github.com/dusty-nv/jetson-inference
$ cd jetson-inference
$ mkdir build
$ cd build
$ cmake ../

## Downloading Models
$ cd jetson-inference/tools
$ ./download-models.sh

## Installing PyTorch 
$ cd jetson-inference/build
$ ./install-pytorch.sh

## Compiling the Project
$ cd jetson-inference/build
$ make
$ sudo make install
$ sudo ldconfig
```

* [Running the Live Camera Recognition Demo](https://github.com/dusty-nv/jetson-inference/blob/master/docs/imagenet-camera-2.md)
* [Running the Live Camera Detection Demo](https://github.com/dusty-nv/jetson-inference/blob/master/docs/detectnet-camera-2.md)
```shell=
$ cd ~/jetson-inference/build/aarch64/bin

## Classifying Images with ImageNet
$ ./imagenet-camera.py --width=640 --height=480 # using GoogleNet, default MIPI CSI camera (640x480)


## Locating Objects with DetectNe
$ ./detectnet-camera.py --network=ssd-inception-v2
$ ./detectnet-camera.py --width=640 --height=480

```
## Tegra-Docker

```shell=
## test gpu status by deviceQuery
$ ~/NVIDIA_CUDA-10.0_Samples/1_Utilities/deviceQuery
$ sudo make
./deviceQuery 

## create arm64 image
$ ~
```