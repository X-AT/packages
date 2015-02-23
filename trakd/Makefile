#
# Copyright (C) 2013-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=xat-trakd
PKG_VERSION:=2015-02-23
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/X-AT/trakd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=d4ededd0d522257e56d31635bc3aa6e233b7dcb8
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.bz2

PKG_LICENSE:=GPLv3

PKG_MAINTAINER:=Vladimir Ermakov <vooon341@gmail.com>

# XXX vala and mavlink actually don't need as runtime dep
# but adding to that list dont work
PKG_BUILD_DEPENDS:=+vala +mavlink vala/host lcm/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/xat-trakd
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=X-AT trakd tracking daemons
  DEPENDS:=+lcm +libgps +udev +glib2
endef

define Package/xat-trakd/description
  X-AT tracking daemons.
endef

# XXX: only for MIPS targets (such as ar71xx)
CMAKE_OPTIONS = -DVALA_EXECUTABLE=$(STAGING_DIR_HOST)/bin/valac \
		-DLCM_GEN=$(STAGING_DIR_HOST)/bin/lcm-gen \
		-DBIG_ENDIAN:BOOL=ON

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
