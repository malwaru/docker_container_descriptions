FROM osrf/ros:humble-desktop-full

USER root
RUN update && sudo apt install locales
RUN  locale-gen en_US en_US.UTF-8
RUN update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
RUN export LANG=en_US.UTF-8

RUN apt install software-properties-common
RUN add-apt-repository universe

RUN apt update && apt upgrade

# nvidia-container-runtime
ENV NVIDIA_VISIBLE_DEVICES \
    ${NVIDIA_VISIBLE_DEVICES:-all}
ENV NVIDIA_DRIVER_CAPABILITIES \
    ${NVIDIA_DRIVER_CAPABILITIES:+$NVIDIA_DRIVER_CAPABILITIES,}graphics



ARG UNAME=humble_user
ARG WS_DIR=/home/$UNAME/humble_ws
ARG UID=1000
ARG GID=1000
RUN groupadd -g $GID -o $UNAME
RUN useradd -m -s /bin/bash -N -u $UID $UNAME && \
    adduser $UNAME sudo && \
    echo "$UNAME ALL=(ALL:ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/$UNAME && \
    mkdir -p $WS_DIR/src &&\
    chown $UNAME:$GID -R $WS_DIR

USER $UNAME
WORKDIR $WS_DIR/src
RUN git clone https://github.com/malwaru/ROS_basics_FC.git
WORKDIR $WS_DIR
# RUN catkin init
# RUN catkin config --extend /opt/ros/noetic/
# RUN catkin build
# RUN echo "source $WS_DIR/devel/setup.bash" >> /home/$UNAME/.bashrc

CMD /bin/bash

