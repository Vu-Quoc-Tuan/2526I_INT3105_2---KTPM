FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive DISPLAY=:0 VNC_PASSWORD=04012005

# x11vnc bám vào display :0
RUN apt-get update && \
    apt-get install -y --no-install-recommends x11vnc && \
    rm -rf /var/lib/apt/lists/*

CMD bash -lc 'exec x11vnc -display :0 -forever -shared -rfbport 5901 -passwd "$VNC_PASSWORD" -noshm -quiet'
