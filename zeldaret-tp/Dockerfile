FROM ghcr.io/pheenoh/devkitppc-gcn:latest
RUN dpkg --add-architecture i386
RUN apt update && apt install build-essential wine wine32 python3 python3-distutils -y

# Install python dependencies
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python3 get-pip.py
RUN python3 -m pip install rich click intervaltree yaz0 numpy capstone aiofiles GitPython requests

# Weird bug with wine results in this needing to be run a second time
RUN dpkg --add-architecture i386
COPY mwcc_compiler/ /tmp/mwcc_compiler
COPY baserom.dol /tmp/baserom.dol

ENTRYPOINT ["tail", "-f", "/dev/null"]