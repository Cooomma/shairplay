#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.61)
AC_INIT([shairplay], [0.9.0], [juhovh@iki.fi])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_SRCDIR([src/shairplay.c])
AC_CONFIG_HEADER([config.h])
AM_INIT_AUTOMAKE([foreign])

# Checks for programs.
AC_PROG_CC
AC_PROG_LIBTOOL

# Checks for libraries.

# Checks for header files.
AC_HEADER_STDC

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.



# Custom check for os, similar to webkit
AC_MSG_CHECKING([for native Win32])
case "$host" in
     *-*-mingw*)
       os_win32=yes
       ;;
     *)
       os_win32=no
       ;;
esac
AC_MSG_RESULT([$os_win32])

case "$host" in
     *-*-linux*)
       os_linux=yes
       ;;
     *-*-freebsd*)
       os_freebsd=yes
       ;;
     *-*-darwin*)
       os_darwin=yes
       ;;
esac

case "$host_os" in
     gnu* | linux* | k*bsd*-gnu)
       os_gnu=yes
       ;;
     *)
       os_gnu=no
       ;;
esac

# OS conditionals
AM_CONDITIONAL([OS_WIN32],[test "$os_win32" = "yes"])
AM_CONDITIONAL([OS_UNIX],[test "$os_win32" = "no"])
AM_CONDITIONAL([OS_LINUX],[test "$os_linux" = "yes"])
AM_CONDITIONAL([OS_GNU],[test "$os_gnu" = "yes"])
AM_CONDITIONAL([OS_FREEBSD],[test "$os_freebsd" = "yes"])

# Custom check for libao
PKG_CHECK_MODULES([libao], [ao >= 1.1.0], [HAVE_LIBAO=1], [HAVE_LIBAO=0])
AM_CONDITIONAL([USE_LIBAO], [test "$HAVE_LIBAO" -eq 1])



AC_CONFIG_FILES(
	[Makefile]
	[include/Makefile]
	[src/Makefile]
	[src/lib/Makefile]
	[src/lib/alac/Makefile]
	[src/lib/crypto/Makefile]
)
AC_OUTPUT