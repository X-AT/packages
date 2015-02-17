#
# Copyright (C) 2013-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xat-trakd
PKG_VERSION:=2015-02-17
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/X-AT/trakd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=f02daabe5b9d9e90fb5352ce6777af20662c7399
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.bz2

PKG_LICENSE:=GPLv3

PKG_MAINTAINER:=Vladimir Ermakov <vooon341@gmail.com>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/xat-trakd
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=X-AT trakd tracking daemons
  DEPENDS:=+lcm +gpsd +udev +glib2 +vala
endef

define Package/xat-trakd/description
  X-AT tracking daemons.
endef

#TARGET_CFLAGS += -ffunction-sections -fdata-sections
#TARGET_LDFLAGS += -Wl,--gc-sections

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr
	$(CP) -rv $(PKG_INSTALL_DIR)/usr/* $(1)/usr
endef

define Package/xat-trakd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,xat-trakd))
