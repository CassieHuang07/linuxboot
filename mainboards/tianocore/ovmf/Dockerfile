FROM golang:1.17

LABEL description="Testing environment for Linuxboot in OVMF"

# Install dependencies
RUN apt update
RUN apt install -y \
	acpica-tools \
	bc \
	bison \
	build-essential \
	cpio \
	flex \
	kmod \
	libelf-dev \
	libncurses5-dev \
	libssl-dev \
	nasm \
	qemu-system \
	uuid-dev

# Get the correct version of UTK
RUN git clone https://github.com/linuxboot/fiano /go/src/github.com/linuxboot/fiano
RUN cd /go/src/github.com/linuxboot/fiano/cmds/utk && GO111MODULE=off go get

# Working directory for mounting git repo in
RUN mkdir /linuxboot-ovmf
WORKDIR /linuxboot-ovmf

ENTRYPOINT ["/bin/bash"]
