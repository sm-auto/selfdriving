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
export PATH=/usr/local/cuda-10.1/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
를 추가해준다.

```
$ source ~/.bashrc
```
추가해준 뒤에 bashrc를 재시작해준다.

### Ubuntu OpenCV 3.31 Install
출처 : https://kkokkal.tistory.com/1328
```
$ sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install ubuntu-restricted-extras

$ sudo apt install build-essential cmake git pkg-config
$ sudo apt install libjpeg-dev libtiff5-dev libjasper-dev libpng-dev
$ sudo apt install libavcodec-dev libavformat-dev libswscale-dev
$ sudo apt install libdc1394-22-dev libxvidcore-dev libx264-dev x264
$ sudo apt install libxine2-dev libv4l-dev v4l-utils
$ sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
$ sudo apt install libgtk-3-dev
$ sudo apt install libatlas-base-dev libeigen3-dev gfortran
$ sudo apt install python3-dev python3-numpy libtbb2 libtbb-dev

$ mkdir ~/opencv
$ cd ~/opencv
$ wget -O opencv-3.3.1.zip https://github.com/opencv/opencv/archive/3.3.1.zip
$ wget -O opencv_contrib-3.3.1.zip https://github.com/opencv/opencv_contrib/archive/3.3.1.zip
$ unzip opencv-3.3.1.zip
$ unzip opencv_contrib-3.3.1.zip

$ mkdir build && cd build

$ cmake \
-D CMAKE_BUILD_TYPE=Release \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D BUILD_WITH_DEBUG_INFO=OFF \
-D BUILD_EXAMPLES=ON \
-D BUILD_opencv_python2=OFF \
-D BUILD_opencv_python3=ON \
-D INSTALL_PYTHON_EXAMPLES=ON \
-D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-3.4.0/modules \
-D WITH_TBB=ON \
-D WITH_V4L=ON \
-D BUILD_opencv_cudacodec=OFF \ # 이 옵션은 error: dynlink_nvcuvid.h no such file or directory가 보이면 해주면 된다.
../opencv-3.3.1/
 
 위 cmake로 안되면 링크에 있는 거로 진행
 
 $ nproc
 위 명령어로 가용할 수 있는 cpu수를 확인 후
 
 $ make -j6 
 숫자 자리에 nproc로 나온 숫자보다 작은 숫자를 넣는다 (2이상)
 
 $ sudo make install
 $ sudo ldconfig
 
 $ pkg-config --modversion opencv
 ```
 마지막 명령어로 opencv 버전이 확인되면 설치완료
 ### ROS Melodic Install
 http://wiki.ros.org/melodic/Installation/Ubuntu
 
 ### (Optional)Anaconda Install
 https://www.anaconda.com/distribution/#download-section
 위 링크에서 아나콘다를 다운받고, 다운받은 디렉토리로 이동한다
 ```
 $ bash Anaconda3-2019.10-Linux-x86_64.sh
 ```
 안내되는 문구를 읽고 설치를 진행하면 된다.
 
 경로는 기본적으로 세팅되어 있는 경로로 설치.
 
 ```
 $ source ~/.bashrc
 ```
 위 명령어로 conda 진입
 
 ```
 $ conda create --name tf python==3.7
 $ conda activate tf
 ```
 'TF'는 제가 지정한 이름으로 아무거나 사용하셔도 무방합니다.
 
 ```
 $ conda install 'PACKAGE_NAME'
 ```
 PACKAGE_NAME에 설치하고싶은 패키지 명들을 적어준다. ex) numpy, scipy, tensorflow, ...
 
 아래는 설치 예제이다.
 ```
 $ conda install numpy
 $ conda insatll matplotlib
 $ conda install -c conda-forge moviepy
 $ conda install tensorflow-gpu==1.14
 $ conda install imageio==2.4.1
 $ conda install scipy==1.1.0
 $ conda install requests
 $ conda install -c conda-forge opencv
 ```
