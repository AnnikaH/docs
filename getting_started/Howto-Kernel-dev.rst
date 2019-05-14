.. _Howto Kernel dev:

Kernel Developers guide
=======================

To build IncludeOS with our conan packages you will need:

- A `Profile <https://github.com/includeos/conan_config/profiles>`__
- Access to our built `conan packages <https://bintray.com/includeos/includeos>`__

To get access to the packages add our bintray remote to your conan remote list:

::

    $ conan remote add includeos https://api.bintray.com/conan/includeos/includeos

.. note::
  We have two channels for our packages in our remote:

  * ``latest`` the latest built package
  * ``stable`` the last stable built package


Compilers
---------

Currently we are building IncludeOS on Linux with ``clang-6.0`` and ``gcc-7.3``.
All our dependencies, libraries and tools found on Bintray are built and tested
with these two compilers.


Cross-Platform Building
^^^^^^^^^^^^^^^^^^^^^^^

To build IncludeOS for MacOS on Linux, you can use the ``clang-6.0-macos-x86_64``
profile.
