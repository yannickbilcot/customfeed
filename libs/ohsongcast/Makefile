#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ohsongcast
PKG_VERSION:=2016-01-26
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/openhome/ohSongcast.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=5d60075c72ddc57f49fe949a044db53ceb137cac
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/ohsongcast
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenHome OhSongcast library
DEPENDS:= +ohtopology +ohnetgenerated
endef

define Package/ohsongcast/description
  OpenHome ohSongcast can be used to provide a virtual soundcard which sends a device's
audio output to another device which implements the OpenHome Receiver service
endef

TARGET_CFLAGS += $(FPIC)

MAKE_FLAGS = CROSS_COMPILE="$(TARGET_CROSS)" \
	includes="-I $(STAGING_DIR)/usr/include/ohNet" \
	ohnetgenerateddir="../ohnetgenerated-1.6.1928/Build/Obj/Posix/Release/" \
	ohnetdir="../ohnet-1.6.2063/Build/Obj/Posix/Release/" \
	prefix=$(PKG_BUILD_DIR)/usr

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)" \
		$(MAKE_FLAGS) release=1 Receiver WavSender
endef

define Package/ohsongcast/install
	$(Package/Install/Default)
endef

$(eval $(call BuildPackage,ohsongcast))
