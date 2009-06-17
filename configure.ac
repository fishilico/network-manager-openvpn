AC_PREREQ(2.52)

AC_INIT(NetworkManager-openvpn, 0.7.0, tim@niemueller.de, NetworkManager-openvpn)
AM_INIT_AUTOMAKE([subdir-objects])
AM_MAINTAINER_MODE

AC_CONFIG_MACRO_DIR([m4])

AC_CONFIG_HEADERS([config.h])

dnl
dnl Require programs
dnl
AC_PROG_CC
AM_PROG_CC_C_O
AC_PROG_INSTALL
AC_PROG_LIBTOOL

dnl
dnl Required headers
dnl
AC_HEADER_STDC
AC_CHECK_HEADERS(fcntl.h paths.h sys/ioctl.h sys/time.h syslog.h unistd.h)

dnl
dnl Checks for typedefs, structures, and compiler characteristics.
dnl
AC_TYPE_MODE_T
AC_TYPE_PID_T
AC_HEADER_TIME

dnl
dnl Checks for library functions.
dnl
AC_PROG_GCC_TRADITIONAL
AC_FUNC_MEMCMP
AC_CHECK_FUNCS(select socket uname)

dnl
dnl GNOME support
dnl
AC_ARG_WITH(gnome, AS_HELP_STRING([--without-gnome], [Build NetworkManager-openvpn without GNOME support, e.g. vpn service only]))
AM_CONDITIONAL(WITH_GNOME, test x"$with_gnome" != xno)

GETTEXT_PACKAGE=NetworkManager-openvpn
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE", [Gettext package])

IT_PROG_INTLTOOL([0.35])
AM_GLIB_GNU_GETTEXT

PKG_CHECK_MODULES(GTHREAD, gthread-2.0)
AC_SUBST(GTHREAD_CFLAGS)
AC_SUBST(GTHREAD_LIBS)

PKG_CHECK_MODULES(DBUS, dbus-glib-1 >= 0.30)
AC_SUBST(DBUS_CFLAGS)
AC_SUBST(DBUS_LIBS)

PKG_CHECK_MODULES(NETWORK_MANAGER, NetworkManager >= 0.7.0 libnm-util >= 0.7.0 libnm_glib libnm_glib_vpn)
AC_SUBST(NETWORK_MANAGER_CFLAGS)
AC_SUBST(NETWORK_MANAGER_LIBS)

if test x"$with_gnome" != xno; then
	PKG_CHECK_MODULES(GTK, gtk+-2.0 >= 2.6)
	AC_SUBST(GTK_CFLAGS)
	AC_SUBST(GTK_LIBS)

	PKG_CHECK_MODULES(GDK_PIXBUF, gdk-pixbuf-2.0)
	AC_SUBST(GDK_PIXBUF_CFLAGS)
	AC_SUBST(GDK_PIXBUF_LIBS)

	PKG_CHECK_MODULES(GLADE, libglade-2.0)
	AC_SUBST(GLADE_CFLAGS)
	AC_SUBST(GLADE_LIBS)

	PKG_CHECK_MODULES(GCONF, gconf-2.0)
	AC_SUBST(GCONF_CFLAGS)
	AC_SUBST(GCONF_LIBS)

	PKG_CHECK_MODULES(GNOMEKEYRING, gnome-keyring-1)
	AC_SUBST(GNOMEKEYRING_CFLAGS)
	AC_SUBST(GNOMEKEYRING_LIBS)
fi

NM_COMPILER_WARNINGS

AC_CONFIG_FILES([
Makefile
src/Makefile
common-gnome/Makefile
auth-dialog/Makefile
properties/Makefile
po/Makefile.in
])
AC_OUTPUT