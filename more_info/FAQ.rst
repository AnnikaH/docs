.. _FAQ:

FAQ
===

General
-------

What compilers do you support?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

IncludeOS is an open source project developed in C++. We support `Clang <https://en.wikipedia.org/wiki/Clang>`__ and
`GCC C <https://en.wikipedia.org/wiki/GNU_Compiler_Collection>`__ compilers.


What build systems are supported?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We mostly develop on linux ``x86_64`` and macos ``x86_64`` systems. But we have support for linux ``x86`` as well. We are currently developing for linux ``aarch64`` systems.


Will IncludeOS run on ARM?
~~~~~~~~~~~~~~~~~~~~~~~~~~

Not yet, but we're working towards that. Please let us know if you've got experience with ARM architecture and time to spare.


Can I compile IncludeOS offline?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, it is possible to compile offline if you have all the required library
packages in your local conan cache.


Packages
--------

How do I install IncludeOS?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

You do not need to install IncludeOS to run a service. We have pre-built
conan packages for `IncludeOS kernel <https://bintray.com/includeos/includeos/includeos%3Aincludeos>`__ that you can use to build your services.

What versions of IncludeOS are available in packages?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

At the moment we store up to 10 latest packages of a library or IncludeOS kernel
unless there are security vulnerabilities found in them.


Can I build an older version of IncludeOS that is no longer available?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, it is possible. The oldest package we
have at the moment on bintray is ``includeos/0.14.1-1088@includeos/latest``.
If you want to build an older version of IncludeOS, checkout to that tag or commit
and see if a `conanfile.py` is available. If it's available you can build IncludeOS
with conan. Otherwise, look at the `README` for that ``tag`` and you should be able
build with the ``install.sh`` script, which was our old way of building the kernel. Please Note that we no longer support those versions.


Can I run several versions of IncludeOS instances?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, you can run applications with several versions of IncludeOS instances.
By default, all our service examples are built with the latest version of
IncludeOS. To build a service with a different version, you can edit the
`conanfile.txt` and under ``[requires]`` you can specify the IncludeOS version
you want to build like this: ``includeos/0.14.0@includeos/latest``.


Development and Contributions
-----------------------------

What if I want to make changes to a package?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can edit a package using ``conan editable``. Have a look at our guide on
how to get :ref:`Editable mode`.

Can I contribute to IncludeOS libraries?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, you may contribute to our libraries, but they need to be verified by our
kernel developers and pass our Jenkins tests before the libraries are updated
and packaged.

Can I use my own external libraries to build IncludeOS?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, you can. You can use your own external libraries or different versions of
a library to build IncludeOS by editing the `conanfile.py` with your package names
and versions you can achieve this. Note that conan follows semantic versioning by
default, thus to mark your own versioning you will need to edit the ``package_id()``
method in the `conanfile.py` to your own versioning choice.
