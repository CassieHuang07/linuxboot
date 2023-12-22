CONTAINER_NAME := linuxboot-mainboards

all:
	echo pick one of debian-packages or repos

debian-packages:
	sudo apt-get install bison flex zlib1g-dev golang build-essential git gcc  isc-dhcp-server tftpd-hpa minicom flashrom
	echo The next command may get an error and that is ok if you have qemu-system-x86_64
	sudo apt-get install qemu-system-x86  

getmecleaner:
	go get -u github.com/u-root/u-root
	go get -u github.com/u-root/cpu/...
	git clone https://github.com/corna/me_cleaner
	@echo Now add $(PWD)/me_cleaner to PATH

docker-build: Dockerfile
	docker build -t $(CONTAINER_NAME) -f $< .

docker-run-amd-rome: docker-build
	docker run --rm -v "$(shell pwd)/amd/rome":/$(CONTAINER_NAME) -w /$(CONTAINER_NAME) $(CONTAINER_NAME) 'make fetch flashkernel'

docker-run-ampere-jade: docker-build
	docker run --rm -v "$(shell pwd)/ampere/jade":/$(CONTAINER_NAME) -w /$(CONTAINER_NAME) $(CONTAINER_NAME) 'make fetch flashkernel'

docker-run-qemu-x86-64: docker-build
	docker run --rm -v "$(shell pwd)/qemu/x86_64":/$(CONTAINER_NAME) -w /$(CONTAINER_NAME) 'make fetch flashkernel'


# buildampere:
# 	docker_run -it -v $PWD:/src -w /src --tmpfs /tmpfs:exec -e HMOE=/src c8106aa1ea23 ./build.sh