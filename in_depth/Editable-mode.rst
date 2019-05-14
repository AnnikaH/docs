.. _Editable mode:

Editable package Mode
=====================

If you are a kernel developer or are simple interested in fiddling with our
kernel code, you can use the includeos package in ``editable`` mode. This is useful
when working with several interconnected components and you would like to test
your changes across several libraries or functionalities.

Below we have written down a few steps to get you started with editable packages.
You can read more about it at `packages in editable mode <https://docs.conan.io/en/latest/developing_packages/editable_packages.html>`__.

.. note::
    Currently this is an experimental feature on conan version 1.13 and they
    have mentioned that for future releases the feature is subject to breaking changes.

To get started with getting the conan package in editable mode,

* Create a ``build`` folder to build IncludeOS

* Edit the ``etc/layout.txt`` : ( **uses jinja2 syntax** ) needed to parse the build folder correctly.

Do some local adaptions for where your build folder is relative to the includeos source folder by setting build_dir in the third line as follows :

::

    {% set simple=true%}

    {% set build_dir='build' %}

    {% if simple==false %}
    {% set arch=settings.arch|string %}
    {% set platform=options.platform|string %}
    {% set build_dir=build_dir+'/'+arch+'/'+platform %}
    {% endif %}

    [bindirs]
    {#This is so that we can find os.cmake after including conanbuildinfo.cmake #}
    cmake

    [includedirs]
    {#This is to ensure the include directory in conanbuildinfo.cmake includes our API#}
    api

    [libdirs]
    {#This is so that we can find our libraries #}
    {{ build_dir }}/plugins
    {{ build_dir }}/drivers
    {{ build_dir }}/lib
    {{ build_dir }}/platform

    [resdirs]
    {#This is so that we can find ldscript and search for drivers plugins etc#}
    {{ build_dir }}

.. note::
    In the non simple form it is possible to have multiple build folders from the same source which allows multiple architectures and configurations to be tested from the same source however the complexity increases


Set package into editable mode
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Make sure to adjust the version to whatever is appropriate.

::

    conan editable add . includeos/$(conan inspect -a version . | cut -d " " -f 2)@includeos/latest --layout=etc/layout.txt


Check Status
~~~~~~~~~~~~

The package is now in **editable mode** and any dependencies of IncludeOS will
pick this IncludeOS package from your local cache. If you make any changes to the
code a simple `make` should be enough. However if your dependencies have changed
you need to redo the `conan install` step.

Here is an example on how it looks when its pulled into cache as editable:

::

    $ conan editable list
    includeos/0.14.1-1052@includeos/latest
    Path: ~/git/IncludeOS
    Layout: ~/git/IncludeOS/etc/layout.txt


Build IncludeOS
~~~~~~~~~~~~~~~

Asuming the buildfolder is build under the includeos source directory the following is enough.
you can also manually perform the build step for the editable package however doing the step below ensures all parameters are transfered correctly from your conan profile and options into the build.

::

    conan install -if build . -pr <conan_profile> (-o options like platform=nano etc)
    conan build -bf build .

*Building small changes once the first build is done*

Once IncludeOS is built by the conan build command you simply have to make sure to issue a make command in the build location

::

    cd build && make
    or
    cmake build --build

Finalizing Changes
~~~~~~~~~~~~~~~~~~

Once the code is *finalized* and you want to verify that the conan package
still builds remove the editable and do a conan create on the package:

::

    $ conan editable remove includeos/0.15.0@includeos/stable
    $ conan create <source_path> includeos/Latest -pr <conan_profile>
