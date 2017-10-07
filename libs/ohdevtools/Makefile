#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ohdevtools
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/openhome/ohdevtools.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE_VERSION:=85f590aea6a350fbdf219fb05a9a1231f084cdc9
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/ohdevtools
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenHome ohdevtools
endef

define Package/ohdevtools/description
  OpenHome ohdevtools.
endef

define Build/Compile
endef

define Package/ohdevtools/install
	$(INSTALL_DIR) $(1)/usr/lib/ohNet
endef

$(eval $(call BuildPackage,ohdevtools))

