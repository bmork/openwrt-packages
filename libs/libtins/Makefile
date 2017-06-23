#
# Copyright (C) 2017 Telenor
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libtins
PKG_VERSION:=3.5
PKG_RELEASE:=1
PKG_MAINTAINER:=Bjørn Mork <bmork@telenor.net>

PKG_SOURCE_URL:=https://github.com/mfontanini/libtins
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v3.5


PKG_LICENSE:=BSD-2-Clause
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

ifneq ($(CONFIG_USE_UCLIBCXX),)
  TARGET_CXX=g++-uc
endif

define Package/libtins
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Network packet sniffing and crafting library
  DEPENDS:=$(CXX_DEPENDS) +libopenssl +libpcap
  URL:=http://libtins.github.io/
endef

define Package/libtins/description
  A high-level, multiplatform C++ network packet sniffing and crafting library.
  Its main purpose is to provide the C++ developer an easy, efficient, platform
  and endianness-independent way to create tools which need to send, receive
  and manipulate network packets.
endef

CMAKE_OPTIONS += -DLIBTINS_ENABLE_CXX11=1 -D_RUN_RESULT_VAR=""

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/tins $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtins.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libtins.pc $(1)/usr/lib/pkgconfig/libtins.pc
	$(SED) \
		's,/usr/include,$$$${prefix}/include,g' \
		$(1)/usr/lib/pkgconfig/libtins.pc
	$(SED) \
		's,/usr/lib,$$$${prefix}/lib,g' \
		$(1)/usr/lib/pkgconfig/libtins.pc
endef

define Package/libtins/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtins.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtins))

