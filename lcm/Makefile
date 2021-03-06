#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lcm
PKG_VERSION:=1.2.1
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/vooon/lcm-vala.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=6c42f49c3efa32d380ca8e34e8d914d8ec9ab680
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.bz2

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
  TITLE:=Lightweight Communications and Marshalling (lcm-vala)
  URL:=http://lcm-proj.github.io/
  DEPENDS:=+glib2
endef

define Package/lcm/description
  LCM is a set of libraries and tools for message passing and data marshalling,
  targeted at real-time systems where high-bandwidth and low latency are critical.
  It provides a publish/subscribe message passing model and
  automatic marshalling/unmarshalling code generation with bindings for applications in a
  variety of programming languages.

  Fork with Vala language support.
endef

HOST_CONFIGURE_ARGS += \
	--without-lua \
	--without-python \
	--without-java \
	--without-vala

CONFIGURE_ARGS += \
	--enable-shared \
	--without-python \
	--without-java \
	--without-lua \
	--with-vala

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) -r $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) -r $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/src
	$(CP) -r $(PKG_INSTALL_DIR)/usr/src/* $(1)/usr/src
endef

define Package/lcm/install
	$(INSTALL_DIR) $(1)/usr/bin
	#$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/lcm-gen $(1)/usr/bin/lcm-gen
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/lcm-logger $(1)/usr/bin/lcm-logger
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/lcm-logplayer $(1)/usr/bin/lcm-logplayer
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,lcm))
