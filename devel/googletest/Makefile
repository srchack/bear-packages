#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=googletest
PKG_VERSION:=1.10.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/google/googletest.git
PKG_SOURCE_VERSION:=703bd9caab50b139428cea1aaff9974ebee5742e

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/googletest
  SECTION:=devel
  CATEGORY:=Development
  TITLE:=googletest
  URL:=https://github.com/google/googletest
endef

define Package/googletest/description
  Google Testing and Mocking Framework
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/{gmock,gtest} $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libgmock*.a $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libgtest*.a $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/cmake/GTest
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/cmake/GTest/*.cmake $(1)/usr/lib/cmake/GTest/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/*.pc $(1)/usr/lib/pkgconfig/
endef

$(eval $(call BuildPackage,googletest))
