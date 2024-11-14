# Use NVIDIA's CUDA image as the base
FROM nvidia/cuda:12.2.0-devel-ubuntu22.04

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    wget \
    python3.10 \
    python3.10-venv \
    python3-pip \
    build-essential \
    sudo \
    google-perftools \
    tmux \ 
    libgl1 \
    libglib2.0-0 \
    python3.10-dev \
    && rm -rf /var/lib/apt/lists/*

# Set Python 3.10 as the default
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1

# Create a non-root user with the same UID and GID as the host user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=1000
ARG USER_PASSWORD=vscode

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo $USERNAME:$USER_PASSWORD | chpasswd \
    && usermod -aG sudo $USERNAME

# Ensure sudo group users are not asked for a password when using sudo command
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# Switch to the new user
USER $USERNAME

# Set the working directory
WORKDIR /workspace

# Copy and install Python dependencies
# COPY requirements_versions.txt .

# RUN python3 -m venv venv
# RUN source venv/bin/activate
# RUN python3 -m pip install --upgrade pip setuptools wheel
# RUN pip install -r requirements_versions.txt
# RUN pip install Cython
# RUN pip install insightface==0.7.3

# Copy the project files

# COPY . .

# Expose the necessary ports
EXPOSE 7860

# Default command
CMD [ "bash" ]