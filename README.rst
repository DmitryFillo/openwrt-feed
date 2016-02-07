====================
Fillo's OpenWrt Feed
====================

I created it for personal use to collect packages with some patches/modules/etc but it's cool if you'll find a desired package here.

.. contents::

Packages
========

* `nginx-sub <https://github.com/DmitryFillo/openwrt-feed/tree/master/net/nginx-sub>`_ (with sub/substitutions support)

How to use
==========

Add the following line to the feeds.conf in the OpenWrt buildroot::

    src-git fillo git://github.com/DmitryFillo/openwrt-feed

Update the feed::

    ./scripts/feeds update fillo

Activate the package::

    ./scripts/feeds install PACKAGE_NAME

Installed packages should now appear in menuconfig.

*If you are building whole OpenWrt, note that you should disable this feed from adding it to the opkg.conf, because there is no pre-compiled packages for any platform. Check Image Configuration -> Separate feed repositories and disable this feed. You can also disable it manually in the opkg.conf after installation. Otherwise you should create your own repository with this feed.*
