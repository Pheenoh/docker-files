FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install wget gpg libxml2 xz-utils make curl pkg-config libarchive13 unzip -y

# Store devkitPro gpg key
RUN mkdir -p /usr/local/share/keyring/
RUN wget -O /usr/local/share/keyring/devkitpro-pub.gpg https://apt.devkitpro.org/devkitpro-pub.gpg

# Add the devkitPro apt repository
RUN echo "deb [signed-by=/usr/local/share/keyring/devkitpro-pub.gpg] https://apt.devkitpro.org stable main" > /etc/apt/sources.list.d/devkitpro.list

RUN apt update
RUN apt install devkitpro-pacman -y

ENV DEVKITPRO=/opt/devkitpro
ENV DEVKITARM=${DEVKITPRO}/devkitARM
ENV DEVKITPPC=${DEVKITPRO}/devkitPPC
ENV PATH=${DEVKITPRO}/tools/bin:$PATH
RUN dkp-pacman -S --noconfirm gamecube-dev
ENTRYPOINT ["tail", "-f", "/dev/null"]