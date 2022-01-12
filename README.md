# micro-ROS-docker-for-Jetson-Nano
This repo is to crate docker images for micro-ROS agent on Nvidia's Jetson Nano. This image is based on ROS2 Foxy.

Steps:
1. Run the docker file in base folder on the repo first

$ cd base

$ docker build -t microros/base:foxy .

2. After the base image is build run the build the dockerfile in micro-ROS-Agent folder

$ cd base

$ docker build -t micro-ros-agent:foxy .

3. Run the docker image

docker run -it --rm -v /dev:/dev --privileged --net=host micro-ros-agent:foxy serial --dev /dev/{device port} -v6
