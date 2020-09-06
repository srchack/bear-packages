#
# Copyright (C) 2020 Yuhei OKAWA <tochiro.srchack@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libhv
PKG_VERSION:=2020-08-08
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/ithewei/libhv.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=cac8ed0b5b2f25677c8aebd0530903a9175768fe
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_VERSION).tar.gz

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_PARALLEL:=1
PKG_FIXUP:=autoreconf
PKG_INSTALL:=0
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk

define Package/libhv
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:= non-blocking IO and timer event loop
  URL:=https://github.com/ithewei/libhv
  DEPENDS:= +libpthread +librt +libstdcpp
endef

define Package/libhv/description
 provides event-loop with non-blocking IO and timer,
 but simpler apis and richer protocols.
endef


TARGET_CFLAGS += -std=c99 -Wall -fpermissive $(FPIC)
TARGET_CXXFLAGS += -std=c++11 -Wall -fpermissive $(FPIC)

MAKE_FLAGS += libhv


define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/hv
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/include/hv/*.{h,hpp} $(1)/usr/include/hv/
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/lib/libhv.{a,so} $(1)/usr/lib/
endef

define Package/libhv/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/lib/libhv.{a,so} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libhv))
