#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ohnetgenerated
PKG_VERSION:=1.6.1928
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/openhome/ohNetGenerated.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=ecb4ec0d0e38d233e02815f2b4a9b06136ea913a
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/ohnetgenerated
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenHome OhNetGenerated library
  DEPENDS:=+ohnet
endef

define Package/ohnetgenerated/description
  OpenHome OhNet Generated proxies and providers for ohMedia and UPnP:AV services.
endef

TARGET_CFLAGS += $(FPIC)

MAKE_FLAGS = CROSS_COMPILE="$(TARGET_CROSS)" \
	native_only=yes \
	ohNetLibDir="$(STAGING_DIR)/usr/lib/ohNet/" \
	inc_build="$(STAGING_DIR)/usr/include/ohNet" \
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
	$(CP) $(PKG_BUILD_DIR)/usr/lib/ohNet/libohNetGenerated*.a $(1)/usr/lib/ohNet/
endef

$(eval $(call BuildPackage,ohnetgenerated))

