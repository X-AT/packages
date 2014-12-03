#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lcm
PKG_VERSION:=1.2.0

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/lcm-proj/lcm.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)

PKG_LICENSE:=LGPL-2.1

PKG_MAINTAINER:=Vladimir Ermakov <vooon341@gmail.com>

HOST_BUILD_DEPENDS:=glib2/host
#PKG_BUILD_DEPENDS:=lcm/host
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/lcm
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Lightweight Communications and Marshalling
  URL:=http://lcm-proj.github.io/
  DEPENDS:=+glib2
endef

define Package/lcm/description
  LCM is a set of libraries and tools for message passing and data marshalling,
  targeted at real-time systems where high-bandwidth and low latency are critical.
  It provides a publish/subscribe message passing model and
  automatic marshalling/unmarshalling code generation with bindings for applications in a
  variety of programming languages.
endef

HOST_CONFIGURE_ARGS += \
	--without-lua \
	--without-python \
	--without-java

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static \
	--without-lua \
	--without-python \
	--without-java

define Package/lcm/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/lcm-gen $(1)/usr/bin/lcm-gen
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/lcm-logger $(1)/usr/bin/lcm-logger
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/lcm-logplayer $(1)/usr/bin/lcm-logplayer
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,lcm))
