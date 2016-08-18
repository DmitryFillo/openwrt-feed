#
# Copyright (C) 2012-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# This is nginx fork from https://github.com/openwrt/packages/tree/cd98970dc84ff72c419d657994965adc7927f98a/net/nginx
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nginx
PKG_VERSION:=1.9.6
PKG_RELEASE:=1

PKG_SOURCE_NAME:=$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE:=$(PKG_SOURCE_NAME).tar.gz
PKG_SOURCE_URL:=http://nginx.org/download/
PKG_MD5SUM:=f6899825e7a8deadba4948ff84515ad6
PKG_MAINTAINER:=Dmitry Fillo <fillo@fillo.me>
PKG_LICENSE:=2-clause BSD-like license

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_NAME)

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

PKG_CONFIG_DEPENDS := \
	CONFIG_NGINX_FILLO_ECHO \
	CONFIG_NGINX_FILLO_HTTP2 \
	CONFIG_NGINX_FILLO_SSL \
	CONFIG_NGINX_FILLO_DAV \
	CONFIG_NGINX_FILLO_FLV \
	CONFIG_NGINX_FILLO_STUB_STATUS \
	CINFIG_NGINX_FILLO_HTTP_SUB \
	CONFIG_NGINX_FILLO_HTTP_CHARSET \
	CONFIG_NGINX_FILLO_HTTP_GZIP \
	CONFIG_NGINX_FILLO_HTTP_SSI \
	CONFIG_NGINX_FILLO_HTTP_USERID \
	CONFIG_NGINX_FILLO_HTTP_ACCESS \
	CONFIG_NGINX_FILLO_HTTP_AUTH_BASIC \
	CONFIG_NGINX_FILLO_HTTP_AUTOINDEX \
	CONFIG_NGINX_FILLO_HTTP_GEO \
	CONFIG_NGINX_FILLO_HTTP_MAP \
	CONFIG_NGINX_FILLO_HTTP_SPLIT_CLIENTS \
	CONFIG_NGINX_FILLO_HTTP_REFERER \
	CONFIG_NGINX_FILLO_HTTP_REWRITE \
	CONFIG_NGINX_FILLO_HTTP_PROXY \
	CONFIG_NGINX_FILLO_HTTP_FASTCGI \
	CONFIG_NGINX_FILLO_HTTP_UWSGI \
	CONFIG_NGINX_FILLO_HTTP_SCGI \
	CONFIG_NGINX_FILLO_HTTP_MEMCACHED \
	CONFIG_NGINX_FILLO_HTTP_LIMIT_CONN \
	CONFIG_NGINX_FILLO_HTTP_LIMIT_REQ \
	CONFIG_NGINX_FILLO_HTTP_EMPTY_GIF \
	CONFIG_NGINX_FILLO_HTTP_BROWSER \
	CONFIG_NGINX_FILLO_HTTP_UPSTREAM_HASH \
	CONFIG_NGINX_FILLO_HTTP_UPSTREAM_IP_HASH \
	CONFIG_NGINX_FILLO_HTTP_UPSTREAM_LEAST_CONN \
	CONFIG_NGINX_FILLO_HTTP_UPSTREAM_KEEPALIVE \
	CONFIG_NGINX_FILLO_HTTP_UPSTREAM_ZONE \
	CONFIG_NGINX_FILLO_HTTP_CACHE \
	CONFIG_NGINX_FILLO_PCRE

include $(INCLUDE_DIR)/package.mk

define Package/nginx-fillo
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=Nginx web server (with additional useful modules)
  URL:=http://nginx.org/
  DEPENDS:=+NGINX_FILLO_PCRE:libpcre +(NGINX_FILLO_SSL||NGINX_FILLO_HTTP_CACHE||NGINX_FILLO_HTTP_AUTH_BASIC):libopenssl +NGINX_FILLO_HTTP_GZIP:zlib +libpthread
  MENU:=1
endef

define Package/nginx-fillo/description
nginx is an HTTP and reverse proxy server, as well as a mail proxy server, written by Igor Sysoev.
With ngx_http_sub_module, nginx_substitutions_filter and nginx_echo_module support.
endef

define Package/nginx-fillo/config
  source "$(SOURCE)/Config.in"
endef

config_files=nginx.conf mime.types fastcgi_params koi-utf koi-win win-utf

define Package/nginx-fillo/conffiles
/etc/nginx/
endef

ADDITIONAL_MODULES:=
ifeq ($(CONFIG_IPV6),y)
  ADDITIONAL_MODULES += --with-ipv6
endif
ifeq ($(CONFIG_NGINX_FILLO_STUB_STATUS),y)
  ADDITIONAL_MODULES += --with-http_stub_status_module
endif
ifeq ($(CONFIG_NGINX_FILLO_FLV),y)
  ADDITIONAL_MODULES += --with-http_flv_module
endif
ifeq ($(CONFIG_NGINX_FILLO_HTTP2),y)
  ADDITIONAL_MODULES += --with-http_v2_module
endif
ifeq ($(CONFIG_NGINX_FILLO_ECHO),y)
  ADDITIONAL_MODULES += --add-module=$(PKG_BUILD_DIR)/echo-nginx-module
endif
ifeq ($(CONFIG_NGINX_FILLO_SSL),y)
  ADDITIONAL_MODULES += --with-http_ssl_module
endif
ifeq ($(CONFIG_NGINX_FILLO_DAV),y)
  ADDITIONAL_MODULES += --with-http_dav_module
endif
ifeq ($(CONFIG_NGINX_FILLO_SUBSTITUTIONS_FILTER),y)
  ADDITIONAL_MODULES += --add-module=$(PKG_BUILD_DIR)/ngx_http_substitutions_filter_module
endif
ifeq ($(CONFIG_NGINX_FILLO_HTTP_SUB),y)
  ADDITIONAL_MODULES += --with-http_sub_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_CACHE),y)
  ADDITIONAL_MODULES += --without-http-cache
endif
ifneq ($(CONFIG_NGINX_FILLO_PCRE),y)
  ADDITIONAL_MODULES += --without-pcre
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_CHARSET),y)
  ADDITIONAL_MODULES += --without-http_charset_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_GZIP),y)
  ADDITIONAL_MODULES += --without-http_gzip_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_SSI),y)
  ADDITIONAL_MODULES += --without-http_ssi_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_USERID),y)
  ADDITIONAL_MODULES += --without-http_userid_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_ACCESS),y)
  ADDITIONAL_MODULES += --without-http_access_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_AUTH_BASIC),y)
  ADDITIONAL_MODULES += --without-http_auth_basic_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_AUTOINDEX),y)
  ADDITIONAL_MODULES += --without-http_autoindex_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_GEO),y)
  ADDITIONAL_MODULES += --without-http_geo_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_MAP),y)
  ADDITIONAL_MODULES += --without-http_map_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_SPLIT_CLIENTS),y)
  ADDITIONAL_MODULES += --without-http_split_clients_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_REFERER),y)
  ADDITIONAL_MODULES += --without-http_referer_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_REWRITE),y)
  ADDITIONAL_MODULES += --without-http_rewrite_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_PROXY),y)
  ADDITIONAL_MODULES += --without-http_proxy_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_FASTCGI),y)
  ADDITIONAL_MODULES += --without-http_fastcgi_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_UWSGI),y)
  ADDITIONAL_MODULES += --without-http_uwsgi_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_SCGI),y)
  ADDITIONAL_MODULES += --without-http_scgi_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_MEMCACHED),y)
  ADDITIONAL_MODULES += --without-http_memcached_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_LIMIT_CONN),y)
  ADDITIONAL_MODULES += --without-http_limit_conn_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_LIMIT_REQ),y)
  ADDITIONAL_MODULES += --without-http_limit_req_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_EMPTY_GIF),y)
  ADDITIONAL_MODULES += --without-http_empty_gif_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_BROWSER),y)
  ADDITIONAL_MODULES += --without-http_browser_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_UPSTREAM_HASH),y)
  ADDITIONAL_MODULES += --without-http_upstream_hash_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_UPSTREAM_IP_HASH),y)
  ADDITIONAL_MODULES += --without-http_upstream_ip_hash_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_UPSTREAM_LEAST_CONN),y)
  ADDITIONAL_MODULES += --without-http_upstream_least_conn_module
endif
ifneq ($(CONFIG_NGINX_FILLO_HTTP_UPSTREAM_KEEPALIVE),y)
  ADDITIONAL_MODULES += --without-http_upstream_keepalive_module
endif

define Build/Configure
	( cd $(PKG_BUILD_DIR) ; \
		./configure \
			--crossbuild=Linux::$(ARCH) \
			--prefix=/usr \
			--conf-path=/etc/nginx/nginx.conf \
			$(ADDITIONAL_MODULES) \
			--error-log-path=/var/log/nginx/error.log \
			--pid-path=/var/run/nginx.pid \
			--lock-path=/var/lock/nginx.lock \
			--http-log-path=/var/log/nginx/access.log \
			--http-client-body-temp-path=/var/lib/nginx/body \
			--http-proxy-temp-path=/var/lib/nginx/proxy \
			--http-fastcgi-temp-path=/var/lib/nginx/fastcgi \
			--with-cc="$(TARGET_CC)" \
			--with-cc-opt="$(TARGET_CPPFLAGS) $(TARGET_CFLAGS)" \
			--with-ld-opt="$(TARGET_LDFLAGS)" \
			--without-http_upstream_zone_module \
	)
endef

define Package/nginx-fillo/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/nginx $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc/nginx
	$(INSTALL_DATA) $(addprefix $(PKG_INSTALL_DIR)/etc/nginx/,$(config_files)) $(1)/etc/nginx/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/nginx.init $(1)/etc/init.d/nginx
endef

define Build/Prepare
	$(call Build/Prepare/Default)
	$(if $(CONFIG_NGINX_FILLO_SUBSTITUTIONS_FILTER),$(call Prepare/ngx_http_substitutions_filter_module))
	$(if $(CONFIG_NGINX_FILLO_ECHO),$(call Prepare/echo_nginx_module))
endef

define Download/ngx_http_substitutions_filter_module
	VERSION:=131c030cbb284c7eb22a1c5184236d0983391441
	SUBDIR:=ngx_http_substitutions_filter_module
	FILE:=nginx-subs-module-$(PKG_VERSION)-$$(VERSION).tar.gz
	URL:=git://github.com/yaoweibin/ngx_http_substitutions_filter_module.git
	PROTO:=git
endef

define Prepare/ngx_http_substitutions_filter_module
	$(eval $(call Download,ngx_http_substitutions_filter_module))
	gzip -dc $(DL_DIR)/$(FILE) | tar -C $(PKG_BUILD_DIR) $(TAR_OPTIONS)
endef

define Download/echo_nginx_module
	VERSION:=02c40f140a6cf1c63478e4175322c91a8bc206e3
	SUBDIR:=echo-nginx-module
	FILE:=echo-nginx-module-$(PKG_VERSION)-$$(VERSION).tar.gz
	URL:=git://github.com/openresty/echo-nginx-module.git
	PROTO:=git
endef

define Prepare/echo_nginx_module
	$(eval $(call Download,echo_nginx_module))
	gzip -dc $(DL_DIR)/$(FILE) | tar -C $(PKG_BUILD_DIR) $(TAR_OPTIONS)
endef

$(eval $(call BuildPackage,nginx-fillo))
