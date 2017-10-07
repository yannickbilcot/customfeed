#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=wiringpi
PKG_VERSION:=2013-10-01
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/limpens/WiringPi.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=102b3c3ef2268aea1640ae86d2242bf342e59bf5
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/wiringpi/Default
  TITLE:=WiringPi library
  URL:=http://wiringpi.com/
endef

define Package/wiringpi
$(call Package/wiringpi/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=@TARGET_brcm2708_RaspberryPi +libpthread
endef

define Package/wiringpi/description
  WiringPi is a GPIO access library written in C for the Raspberry Pi.
endef

define Package/wiringpi-bin
$(call Package/wiringpi/Default)
  TITLE+= (gpio binary)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+wiringpi
endef

define Package/wiringpi-bin/description
  gpio program can be used to control the GPIO pins,
  allowing easy testing of the GPIO interface from the command-line or simple shell scripts.
endef

TARGET_CFLAGS += $(FPIC) -D_GNU_SOURCE

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include/wiringPi}

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libwiringPi.{so*,la,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/include/wiringPi/*.h \
		$(1)/usr/include/wiringPi/
endef

define Package/wiringpi/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/wiringPi/.libs/libwiringPi.so* $(1)/usr/lib/
endef

define Package/wiringpi-bin/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/gpio $(1)/usr/bin/
endef

$(eval $(call BuildPackage,wiringpi))
$(eval $(call BuildPackage,wiringpi-bin))
