FROM osrf/ros:noetic-desktop-full

SHELL ["/bin/bash", "-c"]
RUN apt update && apt upgrade -y
RUN apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential git python3-catkin-tools

WORKDIR /home/catkin_ws/src
RUN git clone https://github.com/scchow/motion_capture_system.git

WORKDIR /home/catkin_ws
RUN source /opt/ros/noetic/setup.bash && catkin build
RUN sed -i '$i\source "/home/catkin_ws/devel/setup.bash"' /ros_entrypoint.sh

ENTRYPOINT ["/ros_entrypoint.sh"]
CMD ["bash"]