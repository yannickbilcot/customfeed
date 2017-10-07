#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sc2mpd
PKG_VERSION:=1.1.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/medoc92/sc2mpd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=96f84e07529338ab49590ce82d15bef20cb22812
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_REMOVE_FILES:=autogen.sh aclocal.m4

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/sc2mpd
  SECTION:=multimedia
  CATEGORY:=Multimedia
  DEPENDS:=+libmicrohttpd +libpthread +libsamplerate +alsa-lib +libstdcpp
  TITLE:=Linn Songcast Receiver/Sender
endef

define Package/sc2mpd/description
  The Sc2mpd package implements gateway between Linn Songcast and Linux systems.
endef

CONFIGURE_ARGS+= \
	--with-build-cc="$(HOSTCC)" \
	--with-openhome="$(BUILD_DIR)"
	--prefix="\usr"

define Package/sc2mpd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/sc2mpd $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mpd2sc $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/scmakempdsender $(1)/usr/bin/
endef

$(eval $(call BuildPackage,sc2mpd))

