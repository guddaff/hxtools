AC_INIT([hxtools], [20121125])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_HEADERS([config.h])
AC_PROG_INSTALL
AM_INIT_AUTOMAKE([-Wall foreign subdir-objects tar-pax no-dist-gzip dist-xz])
AC_PROG_CC
AM_PROG_CC_C_O

AC_CHECK_HEADERS([lastlog.h paths.h])
PKG_CHECK_MODULES([libHX], [libHX >= 3.12.1])
PKG_CHECK_MODULES([libmount], [mount >= 2.20])
PKG_CHECK_MODULES([libpci], [libpci >= 3])
PKG_CHECK_MODULES([libxcb], [xcb >= 1])
AC_SEARCH_LIBS([cap_get_pid], [cap], [libcap_LIBS="$LIBS"; LIBS=""])
AC_SUBST([libcap_LIBS])
AM_CONDITIONAL([HAVE_LIBCAP], [test -n "$libcap_LIBS"])
AC_SEARCH_LIBS([dlopen], [dl], [libdl_LIBS="$LIBS"; LIBS=""])
AC_SUBST([libdl_LIBS])

kbddatadir='${datadir}/kbd';
x11fontdir='${datadir}/fonts';
AC_ARG_WITH([kbddatadir], AS_HELP_STRING([--with-kbddatadir=PATH],
	[Path to the kbd data directory.
	Most likely /usr/share/kbd.]),
	[kbddatadir="$withval"])
AC_ARG_WITH([x11fontdir], AS_HELP_STRING([--with-x11fontdir=PATH],
	[Path to the X11 font directory.
	Most likely /usr/share/fonts.]),
	[x11fontdir="$withval"])
AC_SUBST([kbddatadir])
AC_SUBST([x11fontdir])

regular_CPPFLAGS="-D_FILE_OFFSET_BITS=64 -D_REENTRANT"
regular_CFLAGS="-Wall -Waggregate-return -Wmissing-declarations \
	-Wmissing-prototypes -Wredundant-decls -Wshadow -Wstrict-prototypes \
	-Winline -pipe"
AC_SUBST([regular_CPPFLAGS])
AC_SUBST([regular_CFLAGS])
AC_CONFIG_FILES([Makefile data/Makefile doc/Makefile
	kbd/Makefile sadmin/Makefile sdevel/Makefile smath/Makefile
	smm/Makefile suser/Makefile])
AC_OUTPUT
