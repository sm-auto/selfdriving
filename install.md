## Ubuntu Nvidia Driver Install
```
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt update
$ sudo ubuntu-drivers autoinstall
$ sudo reboot
```

## Ubuntu Nvidia CUDA 10.1 Install
```
$ wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.243_418.87.00_linux.run
$ sudo sh cuda_10.1243.418.87.00_linux.run
```
https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal

위 링크에서 설치해주면 된다.

Install Type은 각자 원하는 대로

설치 과정에서 Nvidia Driver는 선택 해제한 뒤에 그 외 나머지 것들을 설치해주면 된다.

```
$ sudo reboot
$ nvcc -V
```
마지막 명령어로 CUDA 정보가 나온다면 설치 완료

### Ubuntu Nvidia cuDNN Install
https://developer.nvidia.com/cudnn
로그인 후 cuDNN 다운로드 진행

https://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html#installlinux-tar
위 링크에 설치 방법이 있음
```
$ tar -xvzf cudnn-10.1-linux-x64-v7.6.5.32.tgz
$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
$ sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
```
후에 .bashrc 파일 맨 끝에
```
export PATH=/usr/local/cuda-9.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

$ source ~/.bashrc
```
를 추가해준다.
