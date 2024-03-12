FROM mcr.dockerproxy.com/devcontainers/go:1-1.22-bullseye
# 如果在国外
# FROM mcr.microsoft.com/devcontainers/go:1-1.22-bullseye

ARG DEBIAN_FRONTEND=noninteractive
ARG USER=vscode

RUN sed -i "s|http://deb.debian.org/debian|http://mirror.sjtu.edu.cn/debian|g" /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y bash-completion direnv

USER $USER
ARG HOME="/home/$USER"

ENV LANG=C.UTF-8 \
    TZ=Asia/Shanghai \
    PATH="${HOME}/.local/bin:$PATH"

RUN go env -w GO111MODULE=on && \
    go env -w GOPROXY=https://goproxy.cn,direct
#     # 基础开发工具
#     # 一般使用vscode开发都会要求安装这些 tools，也可以使用扩展安装
#     go install github.com/cweill/gotests/gotests@latest && \
#     go install github.com/fatih/gomodifytags@latest && \
#     go install github.com/josharian/impl@latest && \
#     go install github.com/haya14busa/goplay/cmd/goplay@latest && \
#     go install github.com/go-delve/delve/cmd/dlv@latest && \
#     go install honnef.co/go/tools/cmd/staticcheck@latest && \
#     go install golang.org/x/tools/gopls@latest