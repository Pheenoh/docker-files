FROM ghcr.io/zsrtp/devkitppc-gcn:latest

# Install dolphin dependencies
RUN apt update && \
        apt install build-essential \
        software-properties-common \
        ffmpeg \
        libavcodec-dev \
        libavformat-dev \
        libavutil-dev \
        libswscale-dev \
        libevdev-dev \
        libudev-dev \
        libxrandr-dev \
        libxi-dev \
        libpangocairo-1.0-0 \
        qt6-base-dev \
        libqt6svg6 \
        libqt6svg6-dev \
        git \
        cmake \
        ffmpeg \
        libavcodec-dev \
        libevdev-dev \
        libusb-1.0-0-dev \
        libavformat-dev \
        libswscale-dev \
        libsfml-dev \
        libminiupnpc-dev \
        libmbedtls-dev \
        curl \
        libhidapi-dev \
        libgtk2.0-dev \
        libbluetooth-dev \
        portaudio19-dev -y

# Install dolphin
RUN git clone https://github.com/dolphin-emu/dolphin
RUN cd dolphin && \
    git submodule update --init --recursive && \
    mkdir build && \
    cd build && \
    cmake .. -DENABLE_HEADLESS=ON -DENABLE_PULSEAUDIO=OFF -DENABLE_VULKAN=OFF -DENABLE_QT=OFF -DENABLE_ALSA=OFF -DENABLE_LLVM=OFF && make -j$(nproc) && \
    make install

# Install dme-cli
RUN git clone https://github.com/zsrtp/dme-cli
RUN cd dme-cli/Source && \
    mkdir build && \
    cd build && \
    cmake .. && make -j$(nproc) && \
    cp dolphin-memory-engine /usr/bin/dme

ENTRYPOINT ["tail", "-f", "/dev/null"]