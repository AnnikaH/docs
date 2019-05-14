.. _Tools:

Tools, Libraries and Dependencies
=================================

Here we have a list of tools, libraries and other external dependencies used by
IncludeOS. Some are developed by IncludeOS and others are third party dependencies.
Note that for some third party dependencies, IncludeOS has their own fork to make
custom changes needed for the development of IncludeOS.

Tools
-----

The tools and libraries developed by IncludeOS is listed here.

* `Vmrunner <https://github.com/includeos/vmrunner>`__ - Easily boot binaries in qemu
* :ref:`NaCl <NaCl>` - Configuration language for network services
* `Diskbuilder <https://github.com/includeos/diskbuilder>`__
* `Vmbuild <https://github.com/includeos/vmbuild>`__

Libraries
---------

* `MicroLB <https://github.com/includeos/microLB>`__ - Load balancer
* `Mana <https://github.com/includeos/mana>`__ - Web application framework
* `Bucket <https://github.com/includeos/bucket>`__ - Simplified in-memory database

Archived Libraries
------------------

We have a number of libraries here that were developed by us, but are no longer
maintained. Feel free to browse if you are interested in any of them.

* `URI <https://github.com/includeos/uri>`__
* `HTTP <https://github.com/includeos/http>`__
* `Dashboard <https://github.com/includeos/dashboard>`__
* `Cookie <https://github.com/includeos/cookie>`__
* `Path to Regex <https://github.com/includeos/path_to_regex>`__
* `JSON <https://github.com/includeos/json>`__
* `Director <https://github.com/includeos/director>`__
* `Butler <https://github.com/includeos/butler>`__
* `Mender <https://github.com/includeos/mender>`__

External dependencies
---------------------

All of the external dependencies used by IncludeOS are handled by conan. The recipes describing how they are built are kept in a separate repository: `includeos/conan <https://github.com/includeos/conan>`__
