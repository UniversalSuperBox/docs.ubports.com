App development
===============

Welcome to an open source and free platform under constant scrutiny and improvement by a vibrant global community, whose energy, connectedness, talent and commitment is unmatched. Ubuntu is also the third most deployed desktop OS in the world.

But let's be real for a second: Ubuntu Touch app development is not in a great state. The Ubuntu SDK IDE that Canonical created back in the days of yore is majorly out of order. It only works on Ubuntu 16.04, and even there many components are broken.

Luckily, there are some utilities and alternatives that allow us to build click packages for Ubuntu Touch without the huge overhead of QtCreator. This section will give instructions for tools to use and guidance to work around common issues.

Ubuntu UI-Toolkit
-----------------

We decided not to import the documentation pages for all unmaintained components, instead we are working continuously on replacing parts where necessary with more sustainable solutions. The old documentation pages written by Canonical can be found `here <https://docs.ubuntu.com/phone/en/>`_.

* `QML API <https://docs.ubuntu.com/phone/en/apps/api-qml-development/index>`__
* `Cordova HTML5 API <https://docs.ubuntu.com/phone/en/apps/api-html5-development/index>`__

Clickable
---------

`Clickable <https://github.com/bhdouglass/clickable>`__ is a program to support you with developing apps for the Ubuntu Touch platform. It is written by Brian Douglass and helps you to build, manage, install and test your app without the need of the whole Ubuntu SDK.

.. toctree::
    :maxdepth: 1
    :name: toc-appdev-clickable

    clickable/setup
    clickable/cordova

Ubuntu SDK IDE (unsupported)
----------------------------

The `Ubuntu SDK IDE <https://docs.ubuntu.com/phone/en/platform/sdk>`__
is no longer supported by Canonical, and UBports does not currently have
the the time and manpower to get it to a working state.

It can still be installed, but issues are expected::

    sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
    sudo apt update && sudo apt dist-upgrade
    sudo apt install ubuntu-sdk
    sudo reboot # or logout/login
