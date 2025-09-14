FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive DISPLAY=:0

# Xvfb (X server ảo) + XFCE + DBus cho app GUI
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    xvfb xfce4 xfce4-terminal dbus-x11 xauth ca-certificates && \
    rm -rf /var/lib/apt/lists/*

# Start Xvfb (:0) rồi chạy XFCE trong session DBus
CMD bash -lc 'mkdir -p /tmp/.X11-unix && chmod 1777 /tmp/.X11-unix && \
    Xvfb :0 -screen 0 1280x800x24 -nolisten tcp -ac & \
    exec dbus-launch --exit-with-session startxfce4'
