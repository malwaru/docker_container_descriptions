#This DockerFile is not used for this project instead I made new image based on this installed the 
#necessay packages manually. It is avaialble on the dockerhub

FROM malwaru/rnd_v1:hfts

# nvidia-container-runtime
ENV NVIDIA_VISIBLE_DEVICES \
    ${NVIDIA_VISIBLE_DEVICES:-all}
ENV NVIDIA_DRIVER_CAPABILITIES \
    ${NVIDIA_DRIVER_CAPABILITIES:+$NVIDIA_DRIVER_CAPABILITIES,}graphics



ARG UNAME=ros_user
ARG WS_DIR=/home/$UNAME/catkin_ws
RUN echo "source $WS_DIR/devel/setup.bash" >> /home/$UNAME/.bashrc

CMD /bin/bash
