HARDWARE ?=
CLOUD ?=
REGISTRY ?= quay.io
REGISTRY_ORG ?= ai-lab
IMAGE_NAME ?= ${HARDWARE}-bootc
IMAGE_TAG ?= ${CLOUD}-latest

BOOTC_IMAGE_CLOUD ?= ${REGISTRY}/${REGISTRY_ORG}/${IMAGE_NAME}:${IMAGE_TAG}

include $(CLOUD)/Makefile.env

cloud-image:
	podman build \
		$(BOOTC_IMAGE:%=--build-arg BOOTC_IMAGE=%) \
		$(CLOUD:%=--build-arg CLOUD=%) \
		-t ${BOOTC_IMAGE_CLOUD} \
		-f Containerfile \
		.

cloud-disk:
	make -f ../common/Makefile.common bootc-image-builder \
		BOOTC_IMAGE=${BOOTC_IMAGE_CLOUD} \
		DISK_TYPE=${DISK_TYPE} \
		IMAGE_BUILDER_CONFIG=$(CLOUD)/config.toml
