# 基础镜像
FROM mcr.microsoft.com/devcontainers/python:3.11-bullseye

# 安装 mambaforge（最快的 conda 发行版）
RUN curl -sL https://micro.mamba.pm/api/micromamba/linux-64/latest | tar -C /usr/local/bin -xvj bin/micromamba \
  && micromamba shell init -s bash -p /opt/conda

# 复制环境文件并创建环境
COPY environment.yml /tmp/environment.yml
RUN bash -lc "micromamba create -n ml -y -f /tmp/environment.yml"

# 默认激活
ENV MAMBA_DOCKERFILE_ACTIVATE=1
