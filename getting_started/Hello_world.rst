.. _hello world:

Hello World with IncludeOS
==========================

If you would rather build the service using Docker please see:

.. toctree::
  Hello_world_docker

You don't need to manually build IncludeOS to build a service. Our pipeline builds IncludeOS conan packages and uploads them to `bintray <https://bintray.com/beta/includeos/includeos/includeos:includeos>`__.
A service then specifies which version of IncludeOS to use when building.
To get started with the `hello_world` example just clone the service repository:

::

    $ git clone https://github.com/includeos/hello_world
    $ cd hello_world
    $ mkdir your_build_dir && cd "$_"

Then install all the requirements of the service. You will have to select a conan profile to use. Running ``conan profile list`` will show the profiles installed.
- Linux users can typically use ``clang-6.0-linux-x86_64``
- MacOS users can use ``clang-6.0-macos-x86_64``.
You can also develop your own profiles.

::

    $ conan install ../hello_world -pr <your_conan_profile>

Then we activate a virtual environment which sets up the build job with the correct paths. Finally we build using cmake and make. This produces an elf binary that is bootable. The included utility ``boot`` can be used to launch in qemu.

::

    $ source activate.sh
    $ cmake ..
    $ cmake --build .
    $ boot hello

.. note::
    Once you're done ``$ source deactivate.sh`` will reset your environment to
    its previous state.

For more advanced examples see the `examples repo <https://github.com/includeos/demo-examples>`__.
