FROM ubuntu:latest

# đặt múi giờ để tránh lỗi trong quá trình cài đặt, frontend noninteractive sẽ giúp quá trình cài đặt không bị dừng lại để hỏi người dùng
ENV DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC

# cài đặt openssh-server và các gói cần thiết khác
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    openssh-server sudo ca-certificates locales && \
    rm -rf /var/lib/apt/lists/*

# thiết lập locale để tránh các cảnh báo liên quan đến locale - là các thiết lập ngôn ngữ và vùng miền
RUN sed -i 's/^# \(en_US.UTF-8 UTF-8\)/\1/' /etc/locale.gen && locale-gen
ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8

# tạo user vqtuan với mật khẩu vqtuan, thêm user này vào nhóm sudo và tạo thư mục cần thiết cho sshd
RUN useradd -m -s /bin/bash vqtuan && echo "vqtuan:04012005" | chpasswd && \
    usermod -aG sudo vqtuan && \
    mkdir -p /var/run/sshd

# cấu hình sshd để không cho phép đăng nhập root và cho phép xác thực bằng mật khẩu
RUN sed -ri 's/^#?PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config && \
    sed -ri 's/^#?PasswordAuthentication.*/PasswordAuthentication yes/' /etc/ssh/sshd_config

# mở cổng 22 để sshd có thể lắng nghe kết nối
EXPOSE 22

# khởi động sshd khi container được chạy
CMD ["/usr/sbin/sshd","-D"]
