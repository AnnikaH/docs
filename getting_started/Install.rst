.. _Install:

Install
=======

*Introduction*

Dependencies
------------

For building the kernel you will need:

* `C/C++ package manager <https://docs.conan.io/en/latest/installation.html>`__ (Conan 1.13.1 or newer)
* cmake, make, nasm
* clang, or alternatively gcc on linux. Prebuilt packages are available for clang 6.0 and gcc 7.3.

To boot VMs locally you will also need:

* qemu
* python3
* python packages: psutil, jsonschema

Ubuntu installation
-------------------
We are currently developing and testing on ``Ubuntu-18.04``. To get started with
building on Linux, install the following dependencies.

::

    $ apt-get install python3-pip python3-dev git cmake clang-6.0 gcc nasm make qemu
    $ pip3 install setuptools wheel conan psutil jsonschema

macOS installation
------------------
If you have `homebrew <https://brew.sh/>`__ you can use our ``brew tap`` to install the dependencies as follows.

::

    $ brew tap includeos/includeos
    $ brew install includeos

Checkout our `homebrew formula for IncludeOS <https://github.com/includeos/homebrew-includeos>`__

Setting up Conan
----------------
**Getting Conan remotes and profiles**

IncludeOS uses the conan package manager to handle dependencies. To use the profiles and remotes required to use IncludeOS there is an existing conan config repository that can be used.

.. warning::
  This will overwrite any existing conan configuration. To test without touching existing conan configurations set the environment variable ``CONAN_USER_HOME`` to create a separate conan home folder.

To install the IncludeOS conan config issue the following command: 
::

    $ conan config install https://github.com/includeos/conan_config.git

If you prefer to set up conan manually the full configuration can be found in the `conan_config <https://github.com/includeos/conan_config.git>`__ repository.
