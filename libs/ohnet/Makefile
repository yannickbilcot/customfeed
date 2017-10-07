#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ohnet
PKG_VERSION:=1.6.2063
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/openhome/ohNet.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=504e348c18b781f777b95bca7341c8a374c99cf7
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/ohnet
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenHome OhNet library
  DEPENDS:=+libpthread +libstdcpp
endef

define Package/ohnet/description
  OpenHome OhNet library.
endef

TARGET_CFLAGS += $(FPIC)

MAKE_FLAGS = CROSS_COMPILE="$(TARGET_CROSS)" \
	native_only=yes \
	prefix=$(PKG_BUILD_DIR)/usr

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)" \
		$(MAKE_FLAGS)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/ohNet $(1)/usr/include/ohNet
	$(CP) $(PKG_BUILD_DIR)/usr/include/ohNet/* $(1)/usr/include/ohNet/
	$(CP) $(PKG_BUILD_DIR)/usr/lib/ohNet/libohNet.so $(1)/usr/lib/ohNet/
	$(CP) $(PKG_BUILD_DIR)/usr/lib/ohNet/libohNet*.a $(1)/usr/lib/ohNet/
endef

define Package/ohnet/install
	$(INSTALL_DIR) $(1)/usr/lib/ohNet
	$(CP) $(PKG_BUILD_DIR)/usr/lib/ohNet/libohNet.so $(1)/usr/lib/ohNet/
endef

$(eval $(call BuildPackage,ohnet))

