Hacking the Platform
====================

This section aims to help you, the enterprising Ubuntu Touch developer, in your quest to improve the Ubuntu Touch operating system. This is not a section for application developers or porters. It's just for you.

In this section, you'll learn how to download the source of a package for Ubuntu Touch, build and test it on your device, then submit your changes for inclusion in the system images.

Before you begin, you'll need a distribution with the ``qemu-user-static`` and ``debootstrap`` packages. Many distributions have these available, but I'm going to assume that you're using Ubuntu for this guide.

Who owns this package
---------------------

TODO

Download source
---------------

Now that you know that the package is definitely owned by the Ubuntu Touch project, you can download its source from GitHub. Just search for the source on the `UBports GitHub organization`_, fork it, and clone your fork to your computer.

Set up a build environment
--------------------------

You're likely looking to run this package on your Ubuntu Touch device, which is either armhf or arm64. However, your build machine is likely an x86 computer. To get around this problem, we'll use a handy tool called ``qemu-user-static`` to create an armhf build environment for all of your packages.

First, install the required packages::

    sudo apt install -y qemu-user-static debootstrap

Next, create a chroot, replacing ``[ARCH]`` with the architecture of your device::

    sudo qemu-debootstrap --arch [ARCH] xenial chroot

.. note:: If you're not sure of which architecture to choose, see :ref:`which-architecture` below.

Once that's finished, you should be able to move into your real (emulated) system::

    sudo chroot chroot su -

While you're here, you'll probably want to install some tools that we'll need to build almost any package::

    apt install dpkg-dev devscripts

At this point, you can look around and test some commands if you would like. When you're finished, simply type ``exit``.

Bind-mount source
-----------------

In order to access your downloaded source from inside your build chroot, you'll need to bind-mount it into the root user's home directory. To do that, issue the following command::

    sudo mkdir chroot/root/source
    sudo mount --bind [path/to/source] chroot/root/source

Build a package
---------------

Now it's time for what you've been waiting for! Let's build the package.

To start, move into the build chroot again and ``cd`` to the ``source`` directory.

http://iomem.com/archives/18-Avoiding-tests-when-building-Debian-packages.html

Appendices
----------

Cleaning the package directory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Package builds can make a lot of untrakced files that you won't want to commit to the repository. You can clean them up with the following commands::

    TODO

.. _which-architecture:

Which architecture is my device?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Issue the following command via adb or ssh to check the architecture of your device::

    dpkg-architecture -q DEB_HOST_ARCH

.. _UBports GitHub organization: https://github.com/UBports/