# 使用 Ubuntu 作为基础镜像
# FROM yupeng123456/ubuntu:latest
FROM php:8.2-cli

# 安装必要依赖
# RUN apt-get update && \
#		apt-get install -y curl ca-certificates libatomic1 git sudo && \
#		apt-get install -y --no-install-recommends libatomic1 git curl locales language-pack-zh-hans tzdata && \
#		sed -i '/zh_CN.UTF-8/s/^# //g' /etc/locale.gen && \
#		locale-gen zh_CN.UTF-8 && \
#		update-locale LANG=zh_CN.UTF-8 && \
#		rm -rf /var/lib/apt/lists/*
RUN apt update && \
     apt-get install -y --no-install-recommends curl libatomic1 git && \
	 apt-get clean && \
     rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


# 设置环境变量

# 下载并解压官方 VS Code CLI
# ADD vscode_cli_linux_armhf_cli.tar.gz /usr/bin
# RUN cd /usr/bin && \
#		chmod +x code
RUN curl -Lk 'https://code.visualstudio.com/sha/download?build=stable&os=cli-linux-armhf' --output vscode_cli.tar.gz && \
		tar -xf vscode_cli.tar.gz -C /usr/bin && \
		rm vscode_cli.tar.gz
#		echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
# RUN curl -Lk 'https://github.com/YUPENG123/docker/raw/refs/heads/main/vscode-serve-web/vscode_cli_linux_armhf_cli.tar.gz' --output vscode_cli.tar.gz && \

# 创建工作目录
WORKDIR /home/ubuntu

# 暴露服务端口（默认 8000）
EXPOSE 8000

USER  1000:1000

# 启动 Web 服务
# --accept-server-license-terms: 必须接受许可协议
# --without-connection-token: 禁用 Token 验证（生产环境建议开启）
# --host 0.0.0.0: 允许外部访问
CMD ["code", "serve-web", "--accept-server-license-terms", "--host", "0.0.0.0", "--port", "8000", "--without-connection-token"]


