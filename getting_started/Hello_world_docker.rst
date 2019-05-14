.. _hello world docker:

Using Docker
============

To build the hello world service with Docker you must first build the docker container from the IncludeOS repo::

  $ git clone https://github.com/includeos/IncludeOS.git
  $ docker build -t includeos IncludeOS

This creates a Docker container that contains the correct build tools and conan configuration for building a service. It still requires to download the actual conan packages, but that will be completed when building a specific service.

To use the docker container for building the hello world service::

  $ git clone https://github.com/includeos/hello_world.git
  $ cd hello_world
  $ docker run --rm -v $PWD:/service includeos

This will perform the following:

* Create a bind mount of the service files to ``/service`` inside the container
* Run the ``CMD`` from the docker container, which performs:

  * ``conan install`` to download all required conan packages
  * ``cmake ..`` to configure the service
  * ``cmake --build .`` to build the service

The finished service will be available as an elf binary in ``build/hello``.
