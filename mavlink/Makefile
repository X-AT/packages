#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mavlink
PKG_VERSION:=2015-02-12

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/mavlink/c_library.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=7ae438b86ea983e95af5f092e45a5d0f9d093c74

PKG_LICENSE:=LGPL-3

PKG_MAINTAINER:=Vladimir Ermakov <vooon341@gmail.com>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/mavlink
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=MAVLink Micro Air Vehicle Message Marshalling Library (generated headers only)
  URL:=http://mavlink.org
endef

define Package/mavlink/description
  This is a library for lightweight communication between Micro Air Vehicles (swarm) and/or
  ground control stations. It allows for defining messages within XML files,
  which then are converted into appropriate source code for different languages.
  These XML files are called dialects, most of which build on the common dialect provided in common.xml.
endef

define Build/Configure
endef

define Build/Compile
endef

define Build/Install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/mavlink/v1.0
	$(CP) -rv $(PKG_BUILD_DIR)/* $(1)/usr/include/mavlink/v1.0
endef

define Package/mavlink/install
endef

$(eval $(call BuildPackage,mavlink))
