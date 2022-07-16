FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install wget gpg libxml2 xz-utils make curl pkg-config libarchive13 unzip -y
RUN wget https://github.com/devkitPro/pacman/releases/download/v1.0.2/devkitpro-pacman.amd64.deb
RUN dpkg -i devkitpro-pacman.amd64.deb
ENV DEVKITPRO=/opt/devkitpro
ENV DEVKITARM=${DEVKITPRO}/devkitARM
ENV DEVKITPPC=${DEVKITPRO}/devkitPPC
ENV PATH=${DEVKITPRO}/tools/bin:$PATH
RUN dkp-pacman -S --noconfirm gamecube-dev
ENTRYPOINT ["tail", "-f", "/dev/null"]