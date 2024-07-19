##############################################
# 
# OpenWrt Makefile for x86 Gateway Default Settings
#
##############################################
include $(TOPDIR)/rules.mk

PKG_NAME:=x86-Gateway-DefaultConfig
PKG_VERSION:=1.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=utils
  CATEGORY:=Lemonade
  TITLE:=x86 Gateway Default Settings
  MAINTAINER:=Lemonade
  DEPENDS:=+luci-base +luci 
endef

define Package/$(PKG_NAME)/description
        Lemonade's x86 Gateway Default Settings.
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install     #把文件 99-xxx 写入 /etc/uci-defaults/ 目录下，如果是其他文件的话也可以用这种方法把特定文件写入固件中，比如证书
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/default-settings $(1)/etc/uci-defaults/99-$(PKG_NAME)
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/udp2raw_amd64 $(1)/usr/bin/udp2raw
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

