# -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([WoeUSB], [@@WOEUSB_VERSION@@])
AC_CONFIG_SRCDIR([src])
AM_INIT_AUTOMAKE([foreign])
AC_CONFIG_MACRO_DIR([m4])
AM_MAINTAINER_MODE

MY_PACKAGE_INIT([WoeUSB])

AC_LANG([C++])

# Checks for programs.
AC_PROG_CXX
AC_PROG_AWK
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S

# Checks for libraries.
AM_OPTIONS_WXCONFIG
reqwx=@@WOEUSB_VERSION@@
AM_PATH_WXCONFIG($reqwx, wxWin=1)
if test "$wxWin" != 1; then
  AC_MSG_ERROR([
	wxWidgets must be installed on your system.

	Please check that wx-config is in path, the directory
	where wxWidgets libraries are installed (returned by
	'wx-config --libs' or 'wx-config --static --libs' command)
	is in LD_LIBRARY_PATH or equivalent variable and
	wxWidgets version is $reqwx or above.
	])
fi

CPPFLAGS="$CPPFLAGS $WX_CPPFLAGS"
CXXFLAGS="$CXXFLAGS $WX_CXXFLAGS_ONLY"
CFLAGS="$CFLAGS $WX_CFLAGS_ONLY"
LIBS="$LIBS $WX_LIBS"

LT_INIT
AM_PROG_LIBTOOL		dnl indicates that we are using libtool for compilation
AC_PROG_MAKE_SET	dnl indicates that we must have make, which is used by libtool

MY_DETECT_OS dnl Detect OS
MY_INIT_DATA_PATH dnl Define data path for unix / win32 depending on the current target system
AM_FIND_WINDRES dnl Find windres is needed

MY_INIT_DEBUG_SWITCH([false]) dnl Allow building in debug mode ; doesn't edit any cpp options ; true to force debug

MY_FIND_STDCPP

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_CHECK_HEADER_STDBOOL

# Checks for library functions.
AC_CHECK_FUNCS([pow])

AC_CONFIG_FILES([Makefile
                 innoSetup/Makefile
                 src/Makefile
                 src/data/Makefile
                 src/linux-menu/Makefile
                 src/locale/Makefile
                 src/locale/fr/LC_MESSAGES/Makefile
                 src/locale/fr/Makefile
                 src/locale/zh_TW/LC_MESSAGES/Makefile
                 src/locale/zh_TW/Makefile
                 src/win32/Makefile])
AC_OUTPUT
