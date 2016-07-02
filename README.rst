============
OpenWrt Feed
============

I created it for personal use to collect packages with some patches/modules/etc but it's cool if you'll find a desired package here.

.. contents::

Packages
========

* `nginx-fillo <https://github.com/DmitryFillo/openwrt-feed/tree/master/net/nginx-fillo>`_ (with useful additional modules support)

How to use
==========

Add the following line to the feeds.conf in the OpenWrt buildroot::

    src-git fillo git://github.com/DmitryFillo/openwrt-feed;master

Update the feed::

    ./scripts/feeds update fillo

Activate the package::

    ./scripts/feeds install PACKAGE_NAME

Installed packages should now appear in menuconfig.
