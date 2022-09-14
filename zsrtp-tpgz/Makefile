define buildImage
	docker build . -t ghcr.io/pheenoh/zsrtp-tpgz:$(1)
endef

# Set the token in your env before running, otherwise this will fail
define pushImage
	echo $(GHCR_TOKEN) | docker login ghcr.io -u USERNAME --password-stdin
	docker push ghcr.io/pheenoh/zsrtp-tpgz:$(1)
endef

all: build

build:
	@cd base && $(call buildImage,base) && $(call pushImage,base)
	@cd GCN_NTSCU && $(call buildImage,gcn_ntscu) && $(call pushImage,gcn_ntscu)
	@cd GCN_PAL && $(call buildImage,gcn_pal) && $(call pushImage,gcn_pal)
	@cd GCN_NTSCJ && $(call buildImage,gcn_ntscj) && $(call pushImage,gcn_ntscj)
	@cd WII_NTSCU_10 && $(call buildImage,wii_ntscu_10) && $(call pushImage,wii_ntscu_10)
	@cd WII_NTSCU_12 && $(call buildImage,wii_ntscu_12) && $(call pushImage,wii_ntscu_12)
	@cd WII_PAL && $(call buildImage,wii_pal) && $(call pushImage,wii_pal)
	@cd WII_NTSCJ && $(call buildImage,wii_ntscj) && $(call pushImage,wii_ntscj)