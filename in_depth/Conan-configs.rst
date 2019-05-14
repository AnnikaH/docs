.. _Conan configs:

Conan Configuration for IncludeOS
=================================

We have set up a repository `includeos/conan_config <https://github.com/includeos/conan_config>`__ that helps IncludeOS users configure all the necessary conan settings.

.. warning::
  This overwrites any existing conan configuration.
  Thus you should set your ``CONAN_USER_HOME`` to create a separate conan home folder for testing.

To configure using this repo just do:

::

    $ conan config install https://github.com/includeos/conan_config.git


This adds IncludeOS bintray remote in your conan remotes and also installs all the
profiles we have in the repository for you.

Profiles
~~~~~~~~

Conan uses `profiles <https://docs.conan.io/en/latest/reference/profiles.html>`__
to build packages. By default IncludeOS will build with ``clang 6.0`` if
``CONAN_PROFILE`` is not defined. Passing ``-DCONAN_DISABLE_CHECK_COMPILER``
during build disables this check.

Profiles we are developing with can be found in `includeos/conan_config <https://github.com/includeos/conan_config>`__ repository under ``conan_config/profiles/`` .
If you have not used the  ``conan config install`` command above, then to install the profiles, copy them over to your user  ``./conan/profiles`` folder for browse through our `config repo <https://github.com/includeos/conan_config.git>`__ .

The target profiles we have verified are the following:

- `clang-6.0-linux-x86 <https://github.com/includeos/conan_config/tree/master/profiles/clang-6.0-linux-x86>`__
- `clang-6.0-linux-x86_64 <https://github.com/includeos/conan_config/tree/master/profiles/clang-6.0-linux-x86_64>`__
- `gcc-7.3.0-linux-x86_64 <https://github.com/includeos/conan_config/tree/master/profiles/gcc-7.3.0-linux-x86_64>`__
- `clang-6.0-macos-x86_64 <https://github.com/includeos/conan_config/tree/master/profiles/clang-6.0-macos-x86_64>`__

To ensure the profile/s has been installed do:

::

    $ conan profile list


Verify the content of your profile by:

::

    $ conan profile show <yourprofilename>


If your profile is on the list and contents are verified, you are set to use the
profile for building.

IncludeOS Bintray Repository
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The bintray repository is where all the packages used to build IncludeOS
are uploaded. Adding the repo to your conan remotes will give you access to all
our packages developed for IncludeOS.

You can check your repository remotes with:

::

    $ conan remote list


If the includeos remote is not added you have to add it to be able to download
and use packages. Once they are downloaded they are stored in the local cache.

To add the IncludeOS bintray repository to your conan remotes:

::

    $ conan remote add includeos https://api.bintray.com/conan/includeos
