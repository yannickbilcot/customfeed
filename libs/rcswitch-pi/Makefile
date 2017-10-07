#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rcswitch-pi
PKG_RELEASE=$(PKG_SOURCE_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/r10r/rcswitch-pi.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE_VERSION:=2c9c027217ae0b4fe132e0725db166ac29f93974
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

define Package/rcswitch-pi/Default
  TITLE:=rcswitch-pi library
endef

define Package/rcswitch-pi
$(call Package/rcswitch-pi/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=@TARGET_brcm2708_RaspberryPi +wiringpi
endef

define Package/rcswitch-pi/description
  Use rcswitch-pi with your Raspberry Pi to operate remote radio controlled devices.
endef

define Package/rcswitch-pi-bin
$(call Package/rcswitch-pi/Default)
  TITLE+= (send binary)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+rcswitch-pi
endef

define Package/rcswitch-pi-bin/description
  Simple test program for toggling power sockets ON and OFF.
endef

TARGET_CFLAGS += $(FPIC) -D_GNU_SOURCE

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) all
endef

$(eval $(call BuildPackage,rcswitch-pi))
$(eval $(call BuildPackage,rcswitch-pi-bin))

