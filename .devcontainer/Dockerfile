# [Choice] Python version (use -bullseye variants on local arm64/Apple Silicon): 3, 3.10, 3.9, 3.8, 3.7, 3.6, 3-bullseye, 3.10-bullseye, 3.9-bullseye, 3.8-bullseye, 3.7-bullseye, 3.6-bullseye, 3-buster, 3.10-buster, 3.9-buster, 3.8-buster, 3.7-buster, 3.6-buster
ARG VARIANT="jammy"
FROM mcr.microsoft.com/vscode/devcontainers/base:${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    # && apt-get --no-install-recommends -y install <package>  \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
    
# install .Net 8.0 SDK
RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN apt-get update \
    && apt-get install -y apt-transport-https \
    && apt-get install -y dotnet-sdk-8.0

# install Java 21 SDK
RUN  wget https://download.oracle.com/java/21/latest/jdk-21_linux-x64_bin.deb
RUN  dpkg -i jdk-21_linux-x64_bin.deb

# install npm
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - \
    && apt-get install -y nodejs \
    && npm install -g npm@latest 

# install typescript
RUN npm install -g typescript \
    && npm install -g webpack \
    && npm install -g webpack-cli \
    && npm install -g uglifyjs-webpack-plugin \
    && npm install -g @types/jquery \
    && npm install -g http-server \
    && npm install -g eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin \
    && npm install -g forever

# install go
RUN apt update && sudo apt upgrade -y \
    && apt install golang-go -y

# install rust
RUN apt update && sudo apt upgrade -y \
   && apt install curl build-essential gcc make -y \
   && apt install rustc -y

RUN echo 'source /usr/share/bash-completion/completions/git' >> /home/vscode/.bashrc