FROM dustynv/ros:foxy-ros-base-l4t-r32.5.0

RUN mkdir -p uros_ws
WORKDIR uros_ws
RUN git clone --depth 1 -b foxy https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup \
&&  . /opt/ros/foxy/install/setup.sh \
&&  apt update \
&&  apt install -y ed python3-pip \
&&  rosdep update --rosdistro foxy\
&&  rosdep install --from-paths src --ignore-src -y \
&&  colcon build \
&&  rm -rf log/ build/ src/* \
&&  rm -rf /var/lib/apt/lists/*

COPY ./micro-ros_entrypoint.sh /micro-ros_entrypoint.sh

RUN echo ". /opt/ros/foxy/install/setup.bash" >> ~/.bashrc
RUN echo ". /uros_ws/install/setup.bash" >> ~/.bashrc

ENTRYPOINT ["/micro-ros_entrypoint.sh"]
CMD ["bash"]
