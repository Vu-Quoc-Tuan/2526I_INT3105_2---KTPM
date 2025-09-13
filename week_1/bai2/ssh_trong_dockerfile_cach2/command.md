+ Sau khi chạy:
    docker compose up --build -d

+ Vào powershell để kết nối với container
    ssh vqtuan@localhost -p 2222
    nhập pass
    sudo apt update
    sudo apt install -y xfce4 xfce4-terminal tigervnc-standalone-server dbus-x11 xauth x11-xserver-utils
--> tải  và cài đặc vnc server và de

    vncpasswd

    ~$ mkdir -p ~/.vnc
    ~$ cat > ~/.vnc/xstartup <<'EOF'
    ~$ cat ~/.vnc/xstartup
       #!/bin/sh
    unset SESSION_MANAGER
    unset DBUS_SESSION_BUS_ADDRESS
    exec startxfce4
    EOF
    chmod +x ~/.vnc/xstartup
--> Tạo file cấu hình xstartup - script để khởi động gui XFCE desktop

    ~$ vncserver :1 -geometry 1280x800 -localhost no
--> khởi động vnc server

