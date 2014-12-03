#
# Copyright (C) 2013-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=console-bridge
PKG_VERSION:=2014-03-21
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ros/console_bridge.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=b264091d223c396594a573e06aa63731cf694bce
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.bz2

PKG_LICENSE:=BSD

PKG_MAINTAINER:=Vladimir Ermakov <vooon341@gmail.com>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/console-bridge
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Console Bridge
  DEPENDS:=+boost-system +boost-thread
endef

define Package/console-bridge/description
 Console Bridge library.
endef

TARGET_CFLAGS += -ffunction-sections -fdata-sections
TARGET_LDFLAGS += -Wl,--gc-sections
#CMAKE_OPTIONS += $(if $(CONFIG_IPV6),,-DDISABLE_IPV6=1)

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr
	$(CP) -rv $(PKG_INSTALL_DIR)/usr/* $(1)/usr
endef

define Package/console-bridge/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,console-bridge))
