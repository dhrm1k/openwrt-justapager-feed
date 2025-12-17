include $(TOPDIR)/rules.mk

PKG_NAME:=justapager
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/justapager
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Minimal safe pager for appliance CLIs
  DEPENDS:=+libc
endef

define Package/justapager/description
 A minimal, security-focused pager intended for embedded
 systems and appliance CLIs. No shell escapes, no execution.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) \
		-o $(PKG_BUILD_DIR)/justapager \
		$(PKG_BUILD_DIR)/justapager.c
endef

define Package/justapager/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/justapager $(1)/usr/bin/
endef

$(eval $(call BuildPackage,justapager))
