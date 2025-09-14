FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y xfce4 xfce4-terminal tigervnc-standalone-server dbus-x11 xauth sudo && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash vqtuan && echo "vqtuan:04012005" | chpasswd && adduser vqtuan sudo

USER vqtuan
WORKDIR /home/vqtuan

# File xstartup để start XFCE
RUN mkdir -p /home/vqtuan/.vnc
RUN printf '#!/bin/sh\nunset SESSION_MANAGER\nunset DBUS_SESSION_BUS_ADDRESS\nexec startxfce4\n' > /home/vqtuan/.vnc/xstartup \
    && chmod +x /home/vqtuan/.vnc/xstartup

ARG VNC_PASSWORD=04012005
RUN echo "${VNC_PASSWORD}" | vncpasswd -f > ~/.vnc/passwd && chmod 600 ~/.vnc/passwd

EXPOSE 5901
CMD vncserver :1 -geometry 1280x800 -localhost no -fg
