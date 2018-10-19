[![Build Status](https://travis-ci.org/MLAB-project/i2c-tools.svg?branch=master)](https://travis-ci.org/MLAB-project/i2c-tools)

I2C TOOLS FOR LINUX
===================

This package contains an heterogeneous set of I2C tools for the Linux kernel
as well as an I2C library. The tools were originally part of the lm-sensors
project but were finally split into their own package for convenience. The
library is used by some of the tools, but can also be used by third-party
applications. The tools and library compile, run and have been tested on
GNU/Linux on ODROID, Raspberry Pi and Beaglebone boards.

## Changed from original sources
 * By default i2-tools/py-smbus module does not provide an option to forcefully open a i2c-device-address (for safe reasons). But i2get command gives option '-y' to read/write.
 * Added the write_i2c_block and read_i2c_block methods



CONTENTS
--------

The various tools included in this package are grouped by category, each
category has its own sub-directory:

* eeprom
  Perl scripts for decoding different types of EEPROMs (SPD, EDID...) These
  scripts rely on the "eeprom" kernel driver. They are installed by default.

* eeprog, eepromer
  Tools for writing to EEPROMs. These tools rely on the "i2c-dev" kernel
  driver. They are not installed by default.

* include
  C/C++ header files for I2C and SMBus access over i2c-dev. Installed by
  default.

* lib
  The I2C library, used by eeprog, py-smbus and tools. Installed by
  default.

* py-smbus
  Python wrapper for SMBus access over i2c-dev. Not installed by default.

* stub
  A helper script to use with the i2c-stub kernel driver. Installed by
  default.

* tools
  I2C device detection and register dump tools. These tools rely on the
  "i2c-dev" kernel driver. They are installed by default.


LICENSE
-------

Check the documentation of individual tools for licensing information.
The library is released under the LGPL version 2.1 or later, while most
tools are released under the GPL version 2 or later, but there are a few
exceptions.


INSTALLATION
------------

There's no configure script, so simply run "make" to build the library and
tools, and "make install" to install them. You also can use "make uninstall"
to remove all the files you installed. By default, files are installed in
/usr/local but you can change the location by editing the Makefile file and
setting prefix to wherever you want. You may change the C compiler and the
compilation flags as well, and also decide whether to build the static
library or not.

Optionally, you can run "make strip" prior to "make install" if you want
smaller binaries. However, be aware that this will prevent any further
attempt to debug the library and tools.

If you wish to include sub-directories that are not enabled by default, then
just set them via the EXTRA make variable. For example, to build py-smbus,
do:
  $ make EXTRA="py-smbus"


Do not forget to run "sudo ldconfig" after "make install" and "sudo python setup.py install"

DOCUMENTATION
-------------

The main tools have manual pages, which are installed by "make install".
See these manual pages for command line interface details and tool specific
information.

The other tools come with simple text documentation, which isn't installed.


QUESTIONS AND BUG REPORTS
-------------------------

Please post your questions and bug reports to the linux-i2c mailing list:
  linux-i2c@vger.kernel.org
with Cc to the current maintainer:
  Jakub Kakona <kaklik@mlab.cz>
For additional information about this list, see:
  http://vger.kernel.org/vger-lists.html#linux-i2c
