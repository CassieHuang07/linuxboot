FROM ubuntu:latest

LABEL description="Build environment for Linuxboot in mainboards"

# Install dependencies
RUN apt update
RUN apt install -y \
	acpica-tools \
	bc \
	bison \
	build-essential \
	cpio \
	flex \
	gcc-aarch64-linux-gnu \
	gcc-arm-linux-gnueabi \
	gcc-arm-linux-gnueabihf \
	gcc-riscv64-linux-gnu \
	git \
	kmod \
	libelf-dev \
	libncurses5-dev \
	libssl-dev \
	nasm \
	qemu-system \
	uuid-dev \
	u-boot-tools \
	wget

# Get the latest golang version 
# RUN git clone https://github.com/linuxboot/fiano /go/src/github.com/linuxboot/fiano
# RUN cd /go/src/github.com/linuxboot/fiano/cmds/utk && GO111MODULE=off go install

	RUN wget https://golang.org/dl/go1.21.5.linux-amd64.tar.gz
	RUN tar -C /usr/local -xzf go1.21.5.linux-amd64.tar.gz
	ENV PATH=$PATH:/usr/local/go/bin
	ENV GOPATH=$HOME/go
	ENV PATH=$PATH:$GOPATH/bin
	
# Working directory for mounting git repo in
# RUN mkdir /mainboards
# WORKDIR /mainboards
# RUN cd /mainboards

ENTRYPOINT ["/bin/bash"]
