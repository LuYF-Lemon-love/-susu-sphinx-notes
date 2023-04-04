009 Installing Sphinx
=====================

源教程地址: https://example-sphinx-basic.readthedocs.io/en/latest/ .

Overview
--------

Sphinx is written in Python and supports Python 3.8+. 
It builds upon the shoulders of many third-party libraries such as **Docutils** and **Jinja**, 
which are installed when Sphinx is installed.

Linux
-----

**Debian/Ubuntu**

Install either python3-sphinx using apt-get:

.. prompt:: bash

   apt-get install python3-sphinx

If it not already present, this will install Python for you.

**RHEL, CentOS**

Install python-sphinx using yum:

.. prompt:: bash

   yum install python-sphinx

If it not already present, this will install Python for you.

**Other distributions**

Most Linux distributions have Sphinx in their package repositories. 
Usually the package is called python3-sphinx, python-sphinx or sphinx. 
Be aware that there are at least two other packages with sphinx in their name: 
a speech recognition toolkit (CMU Sphinx) and a full-text search database (Sphinx search).

macOS
-----

Sphinx can be installed using Homebrew, MacPorts, 
or as part of a Python distribution such as Anaconda.

**Homebrew**

.. prompt:: bash

   brew install sphinx-doc

For more information, refer to the package overview.

**MacPorts**

Install either python3x-sphinx using port:

.. prompt:: bash

   sudo port install py38-sphinx

To set up the executable paths, use the port select command:

.. prompt:: bash

   sudo port select --set python python38
   sudo port select --set sphinx py38-sphinx

For more information, refer to the package overview.

**Anaconda**

.. prompt:: bash

   conda install sphinx

Windows
-------

Sphinx can be install using Chocolatey or installed manually.

**Chocolatey**

.. prompt:: bash

   choco install sphinx

You would need to install Chocolatey before running this.

For more information, refer to the chocolatey page.

**Other Methods**

Most Windows users do not have Python installed by default, 
so we begin with the installation of Python itself. 
To check if you already have Python installed, open the Command Prompt (⊞Win-r and type cmd). 
Once the command prompt is open, type ``python --version`` and press Enter. 
If Python is installed, you will see the version of Python printed to the screen. 
If you do not have Python installed, 
refer to the Hitchhikers Guide to Python’s Python on Windows installation guides. 
You must install Python 3.

Once Python is installed, you can install Sphinx using pip. 
Refer to the pip installation instructions below for more information.

Installation from PyPI
----------------------

Sphinx packages are published on the Python Package Index. 
The preferred tool for installing packages from PyPI is pip. 
This tool is provided with all modern versions of Python.

On Linux or MacOS, you should open your terminal and run the following command.

.. prompt:: bash

   pip install -U sphinx

On Windows, you should open Command Prompt (⊞Win-r and type cmd) and run the same command.

.. prompt:: batch

   pip install -U sphinx

After installation, type ``sphinx-build --version`` on the command prompt. 
If everything worked fine, 
you will see the version number for the Sphinx package you just installed.

Installation from PyPI also allows you to install the latest development release. 
You will not generally need (or want) to do this, 
but it can be useful if you see a possible bug in the latest stable release. 
To do this, use the ``--pre flag``.

.. prompt:: bash

   pip install -U --pre sphinx

**Using virtual environments**

When installing Sphinx using pip, it is highly recommended to use virtual environments, 
which isolate the installed packages from the system packages, 
thus removing the need to use administrator privileges. 
To create a virtual environment in the ``.venv`` directory, use the following command.

.. prompt:: bash

   python -m venv .venv

You can read more about them in the Python Packaging User Guide.

**Warning**

Note that in some Linux distributions, such as Debian and Ubuntu, 
this might require an extra installation step as follows.

.. prompt:: bash

   apt-get install python3-venv

Docker
------

Docker images for Sphinx are published on the Docker Hub. There are two kind of images:

- `sphinxdoc/sphinx <https://hub.docker.com/r/sphinxdoc/sphinx>`_

- `sphinxdoc/sphinx-latexpdf <https://hub.docker.com/r/sphinxdoc/sphinx-latexpdf>`_

Former one is used for standard usage of Sphinx, 
and latter one is mainly used for PDF builds using LaTeX. Please choose one for your purpose.

**Note** sphinxdoc/sphinx-latexpdf contains TeXLive packages. So the image is very large (over 2GB!).

**Hint**

When using docker images, please use docker run command to invoke sphinx commands. 
For example, you can use following command to create a Sphinx project:

.. prompt:: bash

   docker run -it --rm -v /path/to/document:/docs sphinxdoc/sphinx sphinx-quickstart

And you can use the following command to build HTML document:

.. prompt:: bash

   docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx make html

For more details, please read README file of docker images.

Installation from source
------------------------

You can install Sphinx directly from a clone of the Git repository. 
This can be done either by cloning the repo and installing from the local clone, 
on simply installing directly via git.

.. prompt:: bash

   git clone https://github.com/sphinx-doc/sphinx
   cd sphinx
   pip install .

.. prompt:: bash

   pip install git+https://github.com/sphinx-doc/sphinx

You can also download a snapshot of the Git repo in either ``tar.gz`` or ``zip`` format. 
Once downloaded and extracted, these can be installed with pip as above.