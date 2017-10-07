#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=chacon
PKG_VERSION:=1.0
PKG_RELEASE=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/chacon
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=@TARGET_brcm2708 +libstdcpp +wiringpi
  TITLE:=Chacon power plugs controller
endef

define Package/chacon/description
  This package contains an utility to control Chacon power plugs.
  It works with RF emitter/repector connected to GPIO.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CXX="$(TARGET_CXX)" \
		CXXFLAGS="$(TARGET_CXXFLAGS) -I$(STAGING_DIR)/usr/include/wiringPi" \
		LDFLAGS="$(TARGET_LDFLAGS) -lwiringPi"
endef

define Package/chacon/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/radioSend $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/radioReception $(1)/usr/bin/
endef

$(eval $(call BuildPackage,chacon))

