dnl  This file is an input file used by the GNU "autoconf" program to
dnl  generate the file "configure", which is run during installation
dnl  to configure the system for the local environment.
AC_INIT
AC_CONFIG_SRCDIR([vp_global.h])
AC_CONFIG_HEADERS([config.h])

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
AC_SUBST(OFLAGS)
AC_SUBST(MFLAGS)

AC_PROG_INSTALL
AC_PROG_RANLIB
CC=${CC-cc}
AC_SUBST(CC)

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
AC_PATH_PROGS(M4, gnum4 gm4 m4, m4)

AC_CHECK_HEADERS(string.h memory.h)

AC_FUNC_VPRINTF

AC_CONFIG_FILES([Makefile examples/Makefile])
AC_OUTPUT
