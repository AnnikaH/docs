.. _Howto Service dev:

Service Developers guide
========================

Examples are now built with conan packages. The IncludeOS demo examples have now
been moved to `includeos/demo-examples <https://github.com/includeos/demo-examples.git>`__.

To start build your first service clone the repository:

::

    $ git clone https://github.com/includeos/demo-examples.git
    $ cd demo-examples && ls


You will see a list of all the example services you can try building.

Building a Service
------------------

To build the demo service, create a ``build`` folder inside the ``demo_service`` folder
and install with the profile you would like to use.

::

    $ cd demo_service
    $ mkdir build
    $ cd build
    $ conan install .. -pr <name-of-profile>


Installing with the chosen profile, fetches the profile configurations and Installs
the requirements in the ``conanfile.txt``. If the required packages are not in the
local conan cache they are downloaded and installed. If all the packages required
are already in the local conan cache then it moves on to apply build requirements
and generates the required virtualenv scripts and cmake information.

Next to build the service do:

::

    $ source activate.sh
    $ cmake ..
    $ cmake --build .


Doing ``cmake`` configures and generates the build files and they are written to
the build folder. Then doing ``cmake --build .`` builds the target service. You
should see the last line as:

::

    [100%] Built target demo

``demo`` is the name of this service for the demo_service. That's the name you will
use when starting the service. Do ``ls`` to see all the files created. There is also
an executable file named `demo` which is now the service you will start.


Starting an IncludeOS Instance
------------------------------

Now that you have all your build requirements ready, you can start the service.
If you skipped the step of activating the virtual environment in the previous step remeber to do:

::

    $ source activate.sh


Now you can boot the demo service with ``boot <service-name>``.

::

    $ boot demo


This should start your demo service and show something along the following lines:

::

    ================================================================================
    IncludeOS  (x86_64 / 64-bit)
    +--> Running [ IncludeOS Demo Service ]
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    Service started
    Made device_ptr, adding to machine
      [ Network ] Creating stack for VirtioNet on eth0 (MTU=1500)
         [ Inet ] Bringing up eth0 on CPU 0
    *** Basic demo service started ***


To build more examples follow the `README <https://github.com/includeos/demo-examples/blob/master/README.md>`__ in the examples repository.


Creating your own service
-------------------------

To start writing your first service,

- Copy the `demo_service/service.cpp <https://github.com/includeos/demo-examples/blob/master/demo_service/service.cpp>`__ example.

- Then start implementing the ``Service::start`` function in the ``Service`` class, located in ``<your-service-name>/service.cpp`` (very simple example provided). This function will be called once the OS is up and running.

- Update the ``CMakeLists.txt`` to specify the name of your project, enable any needed drivers or plugins, etc.

- Update the ``conanfile.txt`` to specify any build requirements and generators.

You should then be able to run your service in the same way as the demo_service.

To add a new service to our demo examples, make a PR to our `examples <https://github.com/includeos/demo-examples>`__ repo. Make sure to
add a README in your example folder with description of your service.


.. warning::
  Remember to deactivate your service environment after your work with:

  ``$ source deactivate.sh``
