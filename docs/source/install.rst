Installing Minnal
=================
Prerequisites
-------------
* JDK 7 - Minnal has been tested with Sun JDK and OpenJDK
* `Maven 3 <http://maven.apache.org/download.cgi>`_ 

.. warning::
   Ensure your **JAVA_HOME is set to JDK** and not the JRE. Minnal requires tools.jar from JDK libraries to be in the classpath.

Downloading the package
-----------------------
Current Release
^^^^^^^^^^^^^^^
The current stable release is `2.0.0-rc.1 <https://github.com/minnal/minnal/releases/download/minnal-2.0.0-rc.1/minnal-2.0.0-rc.1.tar.gz>`_

Previous Releases
^^^^^^^^^^^^^^^^^
* `1.2.1 <https://github.com/minnal/minnal/releases/download/minnal-1.2.1/minnal-1.2.1.tar.gz>`_

Extract the downloaded minnal package to a folder with read and write access. Add the the framework binary folder /path/to/minnal-X.X.X/bin to your path, so you can conveniently run the minnal executable. If you are running on windows, add it to the global environment variables. 

Test if you can run minnal,

.. code-block:: bash
   :linenos:

   $ minnal -help

If the installation is proper, you should be able to see the usage. Ensure you have executable permissions for the /path/to/minnal-X.X.X/bin folder

.. code-block:: bash
   :linenos:

   Usage: minnal [options] [command] [command options]
