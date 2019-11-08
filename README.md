# add-apt-repository
sudo apt-get install software-properties-common

# ros visualization
https://github.com/lgsvl/simulator/issues/44


# self-driving using LGSVL and ROS2 crystal

Docker 내부


CUDA 10.1


OpenGL


ROS2 Dashing


ros2-web-bridge

## DOCKER INSTALL <br>

https://docs.docker.com/install/linux/docker-ce/ubuntu/

## NVIDIA-DOCKER INSTALL <br>

https://github.com/NVIDIA/nvidia-docker <br>

nvidia-docker2까지 설치하고 터미널에서 nvidia-docker가 있으면 성공적으로 설치 완료

## nvidia/cuda:10.1-base 설치

docker pull nvidia/cuda:10.1-base

## ros2 dashing(or crystal) install<br>



nvidia-docker run -i -t nvidia/cuda:10.1-base /bin/bash 로 도커 내부로 들어간 뒤

한글(추천) : http://snowdeer.github.io/ros2/2019/02/16/how-to-install-ros2-crystall-using-apt/ <br>
바이너리 : https://index.ros.org/doc/ros2/Installation/Crystal/Linux-Install-Debians/ <br>
빌드 : https://index.ros.org/doc/ros2/Installation/Crystal/Linux-Development-Setup/ <br>

## ros2_bridge install

https://github.com/RobotWebTools/ros2-web-bridge/issues/118#issuecomment-487582528


## x display error
docker run -ti --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix repo-test-3 /bin/bash

nvidia-docker run -it --net=host --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" ksm/ros2:dashing_bridge /bin/bash

## QT
https://tobelinuxer.tistory.com/19
