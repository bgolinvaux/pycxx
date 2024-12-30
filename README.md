PyCXX -- README
===============

Installation using distutils
----------------------------

### Windows Installation and Demo

1.  Fetch <http://prdownloads.sourceforge.net/cxx/pycxx-7.1.8.tar.gz>
2.  Expand the archive into a directory of your choosing C:\ for example.
3.  Install the PyCXX files:
    1.  C:> cd \pycxx-7.1.8

    2.  C:\pycxx-7.1.8> python setup.py install

4.  Build and run the demo extensions:
    1.  C:> cd \pycxx-7.1.8

    2.  C:\pycxx-7.1.8> python setup_makefile.py win32 win32.mak

    3.  C:\pycxx-7.1.8> nmake -f win32.mak clean test

### Unix Installation and Demo

1.  Fetch <http://prdownloads.sourceforge.net/cxx/pycxx-7.1.8.tar.gz>
2.  Login as root. root access is typically needed on Unix systems to install the PyCXX files into the Python directories.
3.  Expand the archive into a directory of your choosing ~\ for example.
4.  Install the PyCXX files:
    1.  # cd ~/pycxx-7.1.8

    2.  # python setup.py install

5.  Build and run the demo extensions:
    1.  # cd ~/pycxx-7.1.8

    2.  # python setup_makefile.py linux linux.mak

    3.  # make -f linux.mak clean test

Revision History
----------------

### Version: 7.1.8 (18-Jun-2023)

Add support for building against python 3.12 beta 1

_Py_PackageContext is no longer accessible.

### Version: 7.1.7 (15-Feb-2022)

This is Version 7.1.6 with README updates

### Version: 7.1.6 (14-Feb-2022)

Add support for building against python 3.11 alpha 4.

### Version: 7.1.5 (21-Feb-2021)

Replace use of deprecated PyUnicode APIs with the supported version.

The class Py::String functions that used deprecated PyUnicode APIs that have no replacements are not available for python 3.9 and later:

    const Py_UNICODE *unicode_data() const;
    unicodestring as_unicodestring() const;

Replace build-all.sh and build-all.cmd with build-all.py that can handle the build matrix.

Add limited API builds for all possible combinations.

Note: Python 3.9 has a bug that prevents use of the limited API until this bug is fix and shipped: [BPO 43155](https://bugs.python.org/issue43155) for details. The workaround is to set Py_LIMITED_API to use python 3.8.

### Version: 7.1.4 (31-May-2020)

Add support for more number methods, like matrix and the inplace versions.

Use IsInstance checking so that derived classes of builtin types can be used.

Update Docs with recent changes.

Add support for python 3.9 beta 1 changes.

### Version: 7.1.3 (8-Jul-2019)

Fix for <https://sourceforge.net/p/cxx/bugs/43/> memory leak caused by wrong ref count on python3 Py::String objects.

Remove support for supportPrint() etc as the tp_print field is being removed from python either in 3.8 or 3.9.

### Version: 7.1.2 (4-Mar-2019)

Fix problem with compiling for Python 2 and the _Py_PackageContext symbol.

Merge Fedora's patch for setup.py

### Version: 7.1.1 (18-Feb-2019)

Add exception errorType() and errorValue() function to access the type and value of an exception.

### Version: 7.1.0 (24-August-2018)

Add support for Py_LIMITED_API aka PEP-384

### Version: 7.0.3 (23-April-2017)

Update Py::Long to support long long consitently between Python2 and Python3.

### Version: 7.0.2 (16-April-2017)

Add Py::Char ord() method to return the long value of a character.

Fix String::size() that could return twice the actual length. This affected as_ucs4string() which would return a string with its second half as uninitialised memory.

Fix setup.py for the Demo code to build all the required C++ code.

### Version: 7.0.1 (29-Aug-2016)

Add extra methods to Py::String that as needed on Windows to support full unicode range of code points.

On Windows Python defines Py_UNICODE as unsigned short, which is too small to hold all Unicode values. PyCXX has added to the Py::String API to support creationg from Py_UCS4 strings and converting Py::String() into Py::ucs4string objects.

Fix validate for Bytes to use the correct check function.

### Version 7.0.0 (15-Aug-2016)

Warning: This version fixes a number of problems that require source incompatible changes.

However by defining PYCXX_6_2_COMPATIBILITY the V6.2.x API is restored. This is not recommended for new code.

The first version of python3 that is supported is 3.3.

A special thanks goes to Benjamin Webb, working at the US Army Engineer Research and Development Center, who has contributed to the design and testing of this release. 7.0.0 is better for his work.

New source file needs to built: Src/cxx_exceptions.cxx. This file implements the new exception handling features.

Fix the type used for lengths and sequence indexes to use Py_ssize_t. This will require sources changes for users of PyCXX.

Implement smart handling of Exceptions between C++ and Python. You can now catch exceptions in C++ by type that are raised in C++ or Python.

All builtin exceptions are support and are user defined exceptions.

The base exception type is now BaseException not Exception. To upgrade source code replace all use of Exception with BaseException.

The documentation has been updated to describe the new exception features.

The supportSequence, supportMapping, supportNumber etc functions now take a bit mask that defines which specific callbacks are handled.

### Version 6.2.8 (10-May-2016)

Fix crash when a member function is called via callMemberFunction() and that function raises an expection.

Found in comment on StackOverFlow. Fix memory size allocated for new objects. It used the wrong size calculation, but was big enough to avoid problems.

### Version 6.2.7 (28-Apr-2016)

Fix missing ptr__Unicode_Type.

Fixes from learn0more@gmail.com make python2 also remember the m_module and add accessor functions.

Fix for indirection issues from Vivian De Smedt.

Update to work with latest Microsoft Visual C++ for python 2.7. All test run in Win32 and Win64.

PyCXX.html documention has been updated, especially with 2TO3 information.

Use delete[] for objects allocated with new[].

### Version 6.2.6 (04-Jan-2015)

Fix build issue with GCC 4.2.1 on FreeBSD and Mac OS X (stop python defining isspace as a macro).

Remove support for python 3.1 (API's are unstable).

Add Python 3.3 support.

Patch from Michael Droettboom to fix compilation issues.

Patch from Michael Droettboom to add buffer interface for python3.

### Version 6.2.4 (3-Mar-2012)

Fix memory leak in string encode and decode functions

Fix indirect python loading on windows - Bool_type was missing

### Version 6.2.3 (11-Mar-2011)

### Version 6.2.2 (26-Dec-2010)

Fix problem compiling against Python 3.1.3

### Version 6.2.1 (3-May-2010)

Fix problems with new style classes

Replace all example makefile and project files with setup_makefile.py script.

Add APIs to make calling python functions easier. See TupleN(), callOnSelf(), self()

### Version 6.1.1 (26-Sep-2009)

Supports Python 3 starting at Python 3.1 and Python 2

Code clean up to fix compiler warnings reported by gcc 4.2.1 on Mac OS X when building for Python 3.

### Version 6.1.0 (19-Jul-2009)

Support Python 3 and Python 2
