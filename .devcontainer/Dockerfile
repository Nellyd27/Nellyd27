# Gunakan image dasar dari ubuntu
FROM mcr.microsoft.com/vscode/devcontainers/base:0-ubuntu-20.04

# Install dependencies dasar
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y \
    curl \
    wget \
    git \
    sudo \
    python3 \
    python3-pip \
    openjdk-11-jre \
    golang

# Install tools bug hunting
RUN apt-get install -y \
    nmap \
    zaproxy \
    nikto \
    sqlmap \
    metasploit-framework \
    wpscan \
    recon-ng \
    sublist3r \
    amass

# Install tools dari Project Discovery
RUN go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest && \
    go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest && \
    go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest && \
    go install -v github.com/projectdiscovery/naabu/v2/cmd/naabu@latest

# Download dan install Burp Suite Community Edition
RUN wget https://portswigger.net/burp/releases/download?product=community&version=2023.4&type=jar -O /usr/local/bin/burpsuite.jar && \
    chmod +x /usr/local/bin/burpsuite.jar

# Setting user permissions
ARG USERNAME=vscode
RUN usermod -aG sudo ${USERNAME}

# Switch to non-root user
USER ${USERNAME}
