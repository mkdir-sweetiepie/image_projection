# Image Projection

## Installation Guide

1. Install Docker

2. Pull Docker image
```bash
docker pull mkdirsweetiepie/fisheye_projection:v4
3.실행
```
xhost +local:root

docker run --runtime=nvidia -it --gpus all --ipc=host \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v $HOME/.Xauthority:/root/.Xauthority \
-e NVIDIA_VISIBLE_DEVICES=all \
-e NVIDIA_DRIVER_CAPABILITIES=all \
-e DISPLAY=$DISPLAY \
-e QT_X11_NO_MITSHM=1 \
--privileged \
--net=host \
--device-cgroup-rule='c 189:* rmw' \
--device-cgroup-rule='c 188:* rmw' \
--name ros1_noetic \
mkdirsweetiepie/fisheye_projection:v1 /bin/bash
```

4.종료는 exit 치면되고 다시 도커 환경 들어올려면
alias do1="xhost +local:root && docker start ros1_noetic && docker exec -it ros1_noetic bash"
gedit bashrc에 넣어 놓고
do1으로 바로 들어가기
