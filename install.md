# Ubuntu Nvidia Driver Install
```
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt update
$ sudo ubuntu-drivers autoinstall
$ sudo reboot
```

# Ubuntu Nvidia CUDA 10.1 Install
```
$ wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.243_418.87.00_linux.run
$ sudo sh cuda_10.1243.418.87.00_linux.run
```
https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal

위 링크에서 설치해주면 된다.

Install Type은 각자 원하는 대로
