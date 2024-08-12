REGISTRY_ORG ?= jpolo
BOOTC_IMAGE_CLOUD=quay.io/$(REGISTRY_ORG)/nvidia-bootc:gcp

cloud:
	podman build \
		$(BOOTC_IMAGE:%=--build-arg BOOTC_IMAGE=%) \
		-t ${BOOTC_IMAGE_CLOUD} \
		-f Containerfile \
		.

disk:
	make -f ../../common/Makefile.common bootc-image-builder \
		BOOTC_IMAGE=${BOOTC_IMAGE_CLOUD} \
		DISK_TYPE=raw \
		IMAGE_BUILDER_CONFIG=$(shell pwd)/config.toml
