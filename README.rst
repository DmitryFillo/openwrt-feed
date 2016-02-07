====================
Fillo's OpenWrt Feed
====================

I created it for personal use to collect packages with some patches/modules/etc but it's cool if you'll find a desired package here.

All packages tested on 15.05.

.. contents::

Packages
========

* `nginx-sub <https://github.com/DmitryFillo/openwrt-feed/tree/master/net/nginx-sub>`_ (with sub/substitutions support)

How to use
==========

Add the following line to the feeds.conf in the OpenWrt buildroot::

    src-git fillo git://github.com/DmitryFillo/openwrt-feed;for-15.05

Update the feed::

    ./scripts/feeds update fillo

Activate the package::

    ./scripts/feeds install PACKAGE_NAME

Installed packages should now appear in menuconfig.
