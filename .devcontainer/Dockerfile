FROM ollama/ollama:latest

RUN groupadd --gid 1000 vscode \
    && useradd -s /bin/bash --uid 1000 --gid 1000 -m vscode \
    && apt-get update \
    && apt-get install -y sudo \
    && echo vscode ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode

RUN apt-get update && \
    apt-get install -y \
    cmake libncurses5-dev libncursesw5-dev git build-essential \
    libdrm-dev libdrm2 libdrm-common linux-libc-dev libsystemd-dev \
    pkg-config libudev-dev libnvidia-ml-dev && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/Syllo/nvtop.git /nvtop && \
    mkdir -p /nvtop/build && \
    cd /nvtop/build && \
    cmake .. \
    -DNVIDIA_SUPPORT=ON -DAMDGPU_SUPPORT=OFF -DINTEL_SUPPORT=OFF \
    -DV3D_SUPPORT=OFF -DMSM_SUPPORT=OFF -DPANFROST_SUPPORT=OFF \
    -DPANTHOR_SUPPORT=OFF && \
    make && make install && \
    cd / && rm -rf /nvtop

RUN echo '#!/bin/bash\nsudo ollama serve && fg\n' > /entrypoint.sh && \
    chmod +x /entrypoint.sh

USER vscode
WORKDIR /home/vscode

ENTRYPOINT ["/entrypoint.sh"]
CMD ["bash"]