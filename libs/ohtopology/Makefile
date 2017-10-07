#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ohtopology
PKG_VERSION:=1.4.1710
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/openhome/ohTopology.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=7847d6611cee7033c35a2fec01bafd6a8b736ed6
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/ohtopology
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenHome OhTopology library
endef

define Package/ohtopology/description
  OpenHome ohTopology provides a view onto devices implementing the OpenHome Media
standard.
endef

define Build/Compile
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/ohNet/OpenHome/Av
	$(CP) $(PKG_BUILD_DIR)/OpenHome/Av/*.h $(1)/usr/include/ohNet/OpenHome/Av/
endef

$(eval $(call BuildPackage,ohtopology))

