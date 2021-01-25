FROM mono:6.12.0.107-slim

RUN apt update && apt install -y mono-complete g++ && rm -rf /var/lib/apt/lists/*

WORKDIR /opt/code
