dnl  This file is an input file used by the GNU "autoconf" program to
dnl  generate the file "configure", which is run during installation
dnl  to configure the system for the local environment.
dnl
dnl Authors:
dnl   Andreas Tille <tille@debian.org> and Daniel Leidert <daniel.leidert@wgdd.de>
dnl License: GPL

dnl Initialize autoconf by any header file of the source
dnl

AC_INIT([volpack],[1.0b3],[volpack@graphics.stanford.edu])
AC_PREREQ([2.71])
AC_CONFIG_SRCDIR([volpack.h])

dnl Define the library SONAME. You can create the different numbers from VERSION
dnl if you want (probably awk, ...)
dnl

LIBVOLPACK_MAJOR=1
LIBVOLPACK_MINOR=1
LIBVOLPACK_MICRO=0

AC_SUBST(LIBVOLPACK_VERSION_INFO, [$LIBVOLPACK_MAJOR:$LIBVOLPACK_MINOR:$LIBVOLPACK_MICRO])

dnl This configures autoheader to generate a config.h file
dnl

AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([-Wall])
m4_ifdef([AM_PROG_AR], [AM_PROG_AR])
LT_INIT

AC_CANONICAL_HOST

case "$host" in
*-irix*)
  test -n "$silent" || echo "choosing compiler flags for SGI Irix"
  OFLAGS="-O -Olimit 2500 -float"
  ;;
*-ultrix*)
  test -n "$silent" || echo "choosing compiler flags for DEC Ultrix"
  OFLAGS="-O -Olimit 2500 -float"
  MFLAGS=
  ;;
*-sunos*)
  test -n "$silent" || echo "choosing compiler flags for SunOS"
  OFLAGS="-O"
  MFLAGS=
  ;;
*-hpux*)
  test -n "$silent" || echo "choosing compiler flags for HP-UX"
  # thanks to Mike Goss (goss@cs.colostate.edu)
  OFLAGS="-Aa +O3 -J +Obb1600"
  MFLAGS="-D_HPUX_SOURCE" 
  ;;
*)
  echo "Unrecognized system type $host.  Using generic compiler options."
  OFLAGS=
  MFLAGS=
  ;;
esac
AC_SUBST([OFLAGS])
AC_SUBST([MFLAGS])

dnl LT_INIT
AC_PROG_CC
dnl CC=${CC-cc}
dnl AC_SUBST(CC)
AC_PROG_CPP
AC_PROG_INSTALL

if test -z "$M4" ; then
  case "$host" in
  *-sunos*)
    AS_MESSAGE([checking /usr/5bin/m4...])
    if test -f /usr/5bin/m4; then
      M4="/usr/5bin/m4"
    fi
    ;;
  esac
fi
AC_PATH_PROGS([M4], [gnum4 gm4 m4])
test -n "$M4" || AC_MSG_ERROR([m4 is missing on your system or not present in PATH.])

AC_CHECK_HEADERS([string.h memory.h])

AC_CHECK_LIB([m], [cos])

AC_FUNC_VPRINTF

AC_CONFIG_FILES([
	Makefile
	doc/Makefile
	examples/Makefile
	man/Makefile
	man/src/Makefile
])
AC_OUTPUT
