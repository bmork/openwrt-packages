#
# Copyright (C) 2017 Telenor
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pping
PKG_VERSION:=0.0
PKG_RELEASE:=1
PKG_MAINTAINER:=Bjørn Mork <bmork@telenor.net>

PKG_SOURCE_URL:=https://github.com/pollere/pping
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=881c665419c215e21e691fcbb582fe8352534ce5

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

ifneq ($(CONFIG_USE_UCLIBCXX),)
  TARGET_CXX=g++-uc
endif

define Package/pping
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Transport Level Passive Ping Monitoring Tool
  DEPENDS:=+libtins
  URL:=http://pollere.net/pping.html
endef

define Package/pping/description
  Unlike ping, pping measures the delay of two different round-trips from the
  packets it monitors, i.e. the round-trip times to the applications at both
  ends of a TCP connection. If pping is co-located with one of the applications,
  it measures delay through the local protocol stack and the application as well
  as the round-trip time to the communicating host. If located along the path,
  e.g. at a WiFi router or a cable modem, delay between the host endpoints can
  be bifurcated with respect to the location of the packet capture. Also unlike
  ping, pping captures all of the flows through it, giving visibility to to the
  various Internet connections to the host. Unlike some other passive metrics,
  pping monitoring can start at any time in the lifetime of a connection, i.e.,
  it does not require SYN packets. 
endef

define Build/Install
endef

define Package/pping/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/pping $(1)/usr/bin/
endef

$(eval $(call BuildPackage,pping))
