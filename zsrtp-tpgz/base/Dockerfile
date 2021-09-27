FROM ghcr.io/pheenoh/devkitppc-gcn:latest

ENV ROMHACK_VERSION=0.0.2

# Install Romhack for linking
RUN wget https://github.com/zsrtp/romhack-compiler/releases/download/${ROMHACK_VERSION}/romhack-${ROMHACK_VERSION}-linux-x64.zip
RUN unzip romhack-${ROMHACK_VERSION}-linux-x64.zip -d .
RUN chmod +x romhack
RUN mv romhack /usr/bin/romhack

# Install Dolphin-Emu
RUN apt update
RUN apt install build-essential ffmpeg libavcodec-dev libavformat-dev libavutil-dev libswscale-dev libevdev-dev libudev-dev libxrandr-dev libxi-dev libpangocairo-1.0-0 qt5-default qtbase5-private-dev git cmake ffmpeg libavcodec-dev libevdev-dev libusb-1.0-0-dev libavformat-dev libswscale-dev libsfml-dev libminiupnpc-dev libmbedtls-dev curl libhidapi-dev libpangocairo-1.0-0 libgtk2.0-dev libbluetooth-dev qt5-default qtbase5-private-dev libudev-dev portaudio19-dev -y
RUN git clone https://github.com/dolphin-emu/dolphin
RUN cd dolphin && mkdir build && cd build && cmake .. -DENABLE_HEADLESS=ON -DENABLE_PULSEAUDIO=OFF -DENABLE_VULKAN=OFF -DENABLE_QT=OFF -DENABLE_ALSA=OFF -DENABLE_LLVM=OFF && make -j$(nproc) && make install

COPY dme /

ENTRYPOINT ["tail", "-f", "/dev/null"]