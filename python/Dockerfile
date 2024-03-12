FROM mcr.dockerproxy.com/devcontainers/python:1-3.9-bullseye
# 如果在国外
# FROM mcr.microsoft.com/devcontainers/python:1-3.9-bullseye

ARG DEBIAN_FRONTEND=noninteractive
ARG USER=vscode

RUN sed -i "s|http://deb.debian.org/debian|http://mirror.sjtu.edu.cn/debian|g" /etc/apt/sources.list && \
    apt update && \
    apt-get install -y default-libmysqlclient-dev direnv

USER $USER
ARG HOME="/home/$USER"
ENV TZ=Asia/Shanghai \
    PATH="${HOME}/.local/bin:$PATH" \
    PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION="python"


RUN pip config set global.index-url https://mirror.sjtu.edu.cn/pypi/web/simple && \
    curl -sSL https://install.python-poetry.org | POETRY_VERSION=1.8.2 python3 - && \
    poetry config virtualenvs.in-project true
