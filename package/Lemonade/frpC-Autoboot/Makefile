##############################################
# 
# OpenWrt Makefile for frpC Automatic Startup
#
##############################################
include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME := frpC-Autoboot
PKG_VERSION := 1.0
PKG_RELEASE := 1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=utils
  CATEGORY:=Lemonade
  TITLE:=frpC Automatic Bootup Script
  MAINTAINER:=Lemonade
endef

define Package/$(PKG_NAME)/description
	Lemonade's frpC Automatic Bootup Script
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/frpC $(1)/etc/init.d/
endef

define Package/$(PKG_NAME)/preinst
	#!/bin/bash
	echo '$(PKG_NAME) installing !'
endef

define Package/$(PKG_NAME)/postinst
	#!/bin/sh
	# check if we are on real system
	if [ -z "$${IPKG_INSTROOT}" ]; then
		echo "Enabling rc.d symlink for $(PKG_NAME)"
		/etc/init.d/frpC enable
	fi

	echo '$(PKG_NAME) symlink enabled !'
	exit 0
endef

define Package/$(PKG_NAME)/postrm
	#!/bin/bash
	echo '$(PKG_NAME) remove successed !'
endef

define Package/$(PKG_NAME)/prerm
	#!/bin/sh
	# check if we are on real system
	if [ -z "$${IPKG_INSTROOT}" ]; then
		echo "Removing rc.d symlink for $(PKG_NAME)"
		/etc/init.d/frpC disable
	fi
	echo '$(PKG_NAME) symlink removed !'
	exit 0
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

