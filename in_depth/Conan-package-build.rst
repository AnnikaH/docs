.. _Conan package build:

Playing with Packages
=====================

If you are interested in editing/building our dependency packages on your own,
you can checkout our repositories at `includeos/ <https://github.com/includeos/>`__ .
You can find the external dependency recipes at `includeos/conan <https://github.com/includeos/conan>`__ .
Currently we build with ``clang-6`` and ``gcc-7.3.0`` compiler toolchains.
It is expected that these are already installed on your system.

.. note::
    Uploaded packages with their recipes can be found on `IncludeOS Bintray <https://bintray.com/includeos/includeos>`__

Building Tools
~~~~~~~~~~~~~~

The **GNU Binutils** are a collection of binary tools we have added to the profiles
so that the binaries are always executable inside the conan environment.
They are not an actual part of the final binary.

The binutils package must be built for the Host it's intended to run on. Therefore
the binutils package is built using a special *toolchain profile* that doesn't have
a requirement on binutils itself.

To build ``bintuils`` using our `includeos/conan <https://github.com/includeos/conan/tree/master/dependencies/gnu/binutils/2.31>`__ recipes:

- Clone the repository
- Do ``conan create`` as follows:

::

    conan create <binutils-conan-recipe-path>/binutils/2.31 -pr <yourprofilename>-toolchain includeos/stable


For MacOS users, we currently have a `apple-clang-10-macos-toolchain <https://github.com/includeos/conan_config/blob/master/profiles/apple-clang-10-macos-toolchain>`__ for building the binutils package.

Building External Dependencies
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To build our other dependencies you may use the conan recipes we have in the
`conan <https://github.com/includeos/conan>`__ repository.

.. note::
    If you plan to build dependencies you might need to ensure you have other missing libraries installed.

**Requirements**

- GNU C++ compiler - ``g++-multilib``
- Secure Sockets Layer toolkit ``libssl-dev``

Building musl
-------------

::

    conan create <conan-recipe-path>/musl/1.1.18 -pr <yourprofilename> includeos/stable



Building llvm stdc++ stdc++abi and libunwind
--------------------------------------------

If these recipes do not have a fixed version in the conan recipe then you have
to specify it alongside the ``user/channel`` as ``package/version@user/channel``
otherwise you can use the same format at musl above.

::

    conan create <conan-recipe-path>/llvm/libunwind -pr <yourprofilename> libunwind/7.0.1@includeos/stable
    conan create <conan-recipe-path>/llvm/libcxxabi -pr <yourprofilename> libcxxabi/7.0.1@includeos/stable
    conan create <conan-recipe-path>/llvm/libcxx -pr <yourprofilename> libcxx/7.0.1@includeos/stable


Building IncludeOS libraries and tools
--------------------------------------

We have moved the libraries and tools created by IncludeOS outside the IncludeOS
repository. You can now find them all in their own repositories inside the IncludeOS
organization.

To build the libraries and tools,

::

    $ git clone https://github.com/includeos/mana.git
    $ cd mana
    $ conan create . includeos/latest -pr clang-6.0-linux-x86_64


Below is a list of some of our Libraries/Tools:

* `Vmbuild <https://github.com/includeos/vmbuild>`__

* `Vmrunner <https://github.com/includeos/vmrunner>`__

* `Mana <https://github.com/includeos/mana>`__

* `Microlb <https://github.com/includeos/microlb>`__

* `Diskbuilder <https://github.com/includeos/diskbuilder>`__

* `NaCl <https://github.com/includeos/NaCl>`__

.. note::
    To get your packages in Editable mode, look at the page on editable package mode.
