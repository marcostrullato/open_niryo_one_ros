FROM ubuntu:16.04
RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install software-properties-common apt-utils git wget
RUN add-apt-repository -y universe
RUN add-apt-repository -y multiverse
RUN add-apt-repository -y restricted
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
RUN apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
RUN apt-get update
RUN apt-get -y install ros-kinetic-desktop-full
RUN rosdep init
RUN rosdep update
RUN echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
RUN apt-get -y install python-rosinstall python-rosinstall-generator python-wstool build-essential ros-kinetic-robot-state-publisher ros-kinetic-moveit ros-kinetic-rosbridge-suite ros-kinetic-joy ros-kinetic-ros-control ros-kinetic-ros-controllers ros-kinetic-tf2-web-republisher nodejs python-pip
RUN pip install --upgrade pip
RUN pip install jsonpickle
RUN mkdir -p /catkin_ws/src; cd /catkin_ws/src; git clone https://github.com/NiryoRobotics/niryo_one_ros.git .
ENV ROS_ROOT=/opt/ros/kinetic/share/ros
ENV ROS_PACKAGE_PATH=/opt/ros/kinetic/share
ENV ROS_MASTER_URI=http://localhost:11311
ENV ROS_VERSION=1
ENV ROSLISP_PACKAGE_DIRECTORIES=
ENV ROS_DISTRO=kinetic
ENV CMAKE_PREFIX_PATH=/opt/ros/kinetic
ENV ROS_ETC_DIR=/opt/ros/kinetic/etc/ros
ENV LD_LIBRARY_PATH=/opt/ros/kinetic/lib:/opt/ros/kinetic/lib/x86_64-linux-gnu
ENV PATH=/opt/ros/kinetic/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV PYTHONPATH=/opt/ros/kinetic/lib/python2.7/dist-packages
ENV PKG_CONFIG_PATH=/opt/ros/kinetic/lib/pkgconfig:/opt/ros/kinetic/lib/x86_64-linux-gnu/pkgconfig
RUN cd /catkin_ws; catkin_make
RUN curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN echo "deb https://deb.nodesource.com/node_8.x $(lsb_release -s -c) main" | tee /etc/apt/sources.list.d/nodesource.list
RUN echo "deb-src https://deb.nodesource.com/node_8.x $(lsb_release -s -c) main" | tee -a /etc/apt/sources.list.d/nodesource.list
RUN cat /etc/apt/sources.list.d/nodesource.list
RUN apt-get install apt-transport-https
RUN apt-get update
RUN apt-get install nodejs
RUN cd /catkin_ws/src/niryo_one_user_interface/blockly_code_generator; npm install; npm link
