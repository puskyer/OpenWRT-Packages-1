
# Copyright (C) 2015 Onion Corporation
#
# Author: Boken Lin <bl@onion.io>
# 
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
PKG_NAME:=gpio-test
PKG_VERSION:=0.1
PKG_RELEASE:=1


PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_URL:=https://github.com/OnionIoT/gpio-test.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=onion
	CATEGORY:=Onion
	SUBMENU:=Utilities
	TITLE:=Utility to test if GPIO IRQ has been setup properly
	DEPENDS:=$(CXX_DEPENDS)
endef


define Package/$(PKG_NAME)/description
Utility to test if GPIO IRQ has been setup properly
endef

define Package/$(PKG_NAME)/Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		LD="$(TARGET_CXX)"
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/bin/gpio-test
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
