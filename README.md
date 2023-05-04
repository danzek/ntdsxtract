ntdsxtract
==========

NTDSXtract - A framework for offline forensic analysis of NTDS.DIT

Active Directory forensic framework

```
--------------------------------------------------------------------------------
 * Description
--------------------------------------------------------------------------------

This framework was developed by the author in order to provide the community
with a solution to extract forensically important information from the main
database of Microsoft Active Directory (NTDS.DIT).

The modules are capable of extracting information from NTDS.DIT files obtained
from the following Windows versions:
 - Windows Server 2003 (32 & 64 bit)
 - Windows Server 2008 (32 & 64 bit)

The code is written in python and tested on the following platforms:
 - MacOS
 - Linux

The framework is capable of extracting information related to:
 - user objects
 - group objects
 - computer objects
 - deleted objects

--------------------------------------------------------------------------------
 * Modules
--------------------------------------------------------------------------------

Currently the following modules are included in the framework:
 - dsfileinformation.py (time and date information related to the NTDS.DIT
                         database file)
 - dstimeline.py        (timeline generation module)
 - dsdeletedobjects.py  (module that can extract information related to
                         deleted objects)
 - dsusers.py           (extracts information related to user objects)
 - dsgroups.py          (extracts information related to group objects)
 - dscomputers.py       (extracts information related to computer objects)
 - dskeytab.py          (extracts information that can be used to decrypt the
                         kerberos network traffic - by Sergey Kubasov)

--------------------------------------------------------------------------------
 * Usage
--------------------------------------------------------------------------------

In order to utilise the framework you should compile and install the libesedb
library (see below). After that you should run the esedbextract tool against the
NTDS.DIT file and export all the tables. You can do that with the following
command:

  esedbexport ntds.dit

This command creates a folder in the current directory called ntds.dit.extract.
Inside that folder you will find the tables. You should use these tables as an
input to the modules.

In order to extract password hashes and other encrypted data you should obtain
the registry from the same domain controller from which the file NTDS.DIT was
extracted.

--------------------------------------------------------------------------------
 * Videos
--------------------------------------------------------------------------------

You can find some videos of the framework in action here.
 - [dsfileinformation.py module](https://github.com/danzek/ntdsxtract/raw/master/resources/dsfileinformation.mov)
 - [dstimeline.py module](https://github.com/danzek/ntdsxtract/raw/master/resources/dstimeline.mov)
 - [dsdeletedobjects.py module](https://github.com/danzek/ntdsxtract/raw/master/resources/dsdeletedobjects.mov)
 - [dsusers.py module](https://github.com/danzek/ntdsxtract/raw/master/resources/dsusers.mov)
 - [dsgroups.py module](https://github.com/danzek/ntdsxtract/raw/master/resources/dsgroups.mov)
 - [dscomputers.py module](https://github.com/danzek/ntdsxtract/raw/master/resources/dscomputers.mov)

--------------------------------------------------------------------------------
 * Requirements
--------------------------------------------------------------------------------

In order to use the framework the excellent library called libesedb must be
installed. The moudles extracts information from the output of the tool
esedbextract which is included in this library. The code of the library can
be downloaded from:

  http://sourceforge.net/projects/libesedb/ (now available at [https://github.com/libyal/libesedb](https://github.com/libyal/libesedb))

Some part of the framework is based on the excellent framework called creddump.
You can download the lates version of creddump from

  http://code.google.com/p/creddump/ ([forked on GitHub](https://github.com/danzek/creddump))

```
