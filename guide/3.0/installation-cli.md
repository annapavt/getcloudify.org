---
layout: bt_wiki
title: Installing Cloudify CLI
category: Installation
publish: true
abstract: Installation instructions for Cloudify CLI under multiple platforms
pageord: 22

windows_link: http://gigaspaces-repository-eu.s3.amazonaws.com/org/cloudify3/3.0.0/nightly_6/cloudify-cli_3.0.0-ga-b6.exe
linux32_link: http://gigaspaces-repository-eu.s3.amazonaws.com/org/cloudify3/3.0.0/nightly_6/cloudify-cli_3.0.0-ga-b6_i386.deb
linux64_link: http://gigaspaces-repository-eu.s3.amazonaws.com/org/cloudify3/3.0.0/nightly_6/cloudify-cli_3.0.0-ga-b6_amd64.deb
venv_link: http://virtualenv.readthedocs.org/en/latest/
---
{%summary%}{{page.abstract}}{%endsummary%}

Cloudify CLI is being distributed in two different methods:

1. As a binary package
1. As a Python package (via PyPi)

Installation via a binary package is recommended for all users that do not have
any intent to use Cloudify CLI for development purpose.

# Installing the binary package

## Windows

1. Download the [Setup file]({{ page.windows_link }})
1. Run the setup file by double clicking on it.
1. Click 'Next'
1. Choose the path you would like the CLI to be installed at and click 'Next'.
Default path is `C:\Program Files (x86)\cfy`
1. To use the CLI you need the folder to be in your PATH environment variable. If
you leave the checkbox checked, the installer will modify the PATH environment
variable for you. Click 'Next' again.
1. Click 'Install' to proceed with file extraction.
1. After a few seconds, installation should be finished, and you can click 'Finish'.
1. Open a new Command Prompt and check if you can run `cfy -h`. You should get
an output describing how to use `cfy`.

## Ubuntu

1. Download a deb package that matches your system:
[32bit]({{ page.linux32_link }}) or
[64bit]({{ page.linux64_link }})
1. Open a Terminal at the directory where you downloaded the file and run
`sudo dpkg -i <pkg.deb>` replacing `<pkg.deb>` with the name of file you downloaded.
1. After a few seconds installation should finish.
1. Try running `cfy -h` command in your Terminal. You should get an output
describing how to use `cfy`.

## OS X

Coming soon, please follow the Python package installation below ([Installing from PyPi](#installing-from-pypi)). 

# Installing from PyPi

Installation via PyPi is intended mostly for development purposes. We'll assume you
have Python and PIP installed and configured on your system.

To install run the following command: 

{% highlight bash %}
pip install cloudify-cli
{% endhighlight %}

{%note title=Note%}
It's recommended to create a [virtualenv]({{ page.venv_link }}) and install the CLI in it. To do so type the following commands (replace virtual-env-name with the name of your choice, e.g. cloudify: 

```
virtualenv virtual-env-name
cd /virtual-env-name
source bin/activate
```

{%endnote%}

## Prerequisites for Compilation

Cloudify CLI has dependencies that require compilation on your machine:

### Windows

For Windows it's suggested to use [Unofficial Windows Binaries for Python](http://www.lfd.uci.edu/~gohlke/pythonlibs)
and install the following packages:

1. PyCrypto
2. PyYaml

### Linux

Under Ubuntu, you'll need to install the `python-dev` package.

### OS X

You will need Apple's developers tools that are installed with Xcode.

{% note title=Note for Mac users %} One of the libraries that's installed with the OpenStack provider (`pycrypto`) may fail to compile on certain variations of OS X. This seems to be a [known issue](http://stackoverflow.com/questions/19617686/trying-to-install-pycrypto-on-mac-osx-mavericks/22868650#22868650). To solve it, type the following command in your terminal windows and try the installation again: 

{% highlight bash %}
export CFLAGS=-Qunused-arguments
export CPPFLAGS=-Qunused-arguments
{% endhighlight %}

{% endnote %}





