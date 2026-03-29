#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.59])

AC_INIT([mac-robber], [1.02], [Brian Carrier <carrier@sleuthkit.org>])
AC_CONFIG_SRCDIR([mac-robber.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIRS([m4])

# Invoke automake:
AM_INIT_AUTOMAKE([foreign])

# Checks for programs.
AC_PROG_CC

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h string.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_MODE_T

# Checks for library functions.
AC_FUNC_LSTAT_FOLLOWS_SLASHED_SYMLINK
AC_FUNC_MALLOC
AC_CHECK_FUNCS([gethostname])


# Introduce a debug mode:
AC_ARG_ENABLE([debug],
	[  --enable-debug    Turn on debugging],
	[case "${enableval}" in
		yes) debug=true ;;
		no)  debug=false ;;
		*) AC_MSG_ERROR([bad value ${enableval} for --enable-debug]) ;;
	esac],
	[debug=false])
AM_CONDITIONAL([DEBUG], [test x$debug = xtrue])


# Offer the possibility to build it in a shared (non-static) way:
AC_ARG_ENABLE([shared],
	[  --enable-shared   Build it in a shared (non-static) way (default is: build it statically)],
	[case "${enableval}" in
		yes) shared=true ;;
		no)  shared=false ;;
		*) AC_MSG_ERROR([bad value ${enableval} for --enable-shared]) ;;
	esac],
	[shared=false])
AM_CONDITIONAL([SHARED], [test x$shared = xtrue])


# Get the canonical host variables:
AC_CANONICAL_HOST 


# Set certain flags depending on the architecture of the build host:
case $host in
  *sun*) MAC_ROBBER_CFLAGS=''
	       MAC_ROBBER_CFLAGS_DEBUG=''
	       MAC_ROBBER_CPPFLAGS='' 
		     MAC_ROBBER_LDFLAGS_STATIC='-Bstatic'
		     MAC_ROBBER_LDFLAGS_SHARED='' ;;

	*linux*) MAC_ROBBER_CFLAGS='-O3 -Wall'
	       MAC_ROBBER_CFLAGS_DEBUG='-O0 -ggdb -Wall'
	       MAC_ROBBER_CPPFLAGS='-D_FILE_OFFSET_BITS=64'
		     MAC_ROBBER_LDFLAGS_STATIC='-static'
		     MAC_ROBBER_LDFLAGS_SHARED='' ;;

    *darwin*) MAC_ROBBER_CFLAGS='-O3 -Wall'
	       MAC_ROBBER_CFLAGS_DEBUG='-O0 -ggdb -Wall' 
	       MAC_ROBBER_CPPFLAGS='' 
		     MAC_ROBBER_LDFLAGS_STATIC=''
		     MAC_ROBBER_LDFLAGS_SHARED='' ;;

  *)     MAC_ROBBER_CFLAGS='-O3 -Wall'
	       MAC_ROBBER_CFLAGS_DEBUG='-O0 -ggdb -Wall' 
	       MAC_ROBBER_CPPFLAGS='' 
		     MAC_ROBBER_LDFLAGS_STATIC='-static'
		     MAC_ROBBER_LDFLAGS_SHARED='' ;;
esac

AC_SUBST([MAC_ROBBER_CFLAGS])
AC_SUBST([MAC_ROBBER_CFLAGS_DEBUG])
AC_SUBST([MAC_ROBBER_CPPFLAGS])
AC_SUBST([MAC_ROBBER_LDFLAGS_STATIC])
AC_SUBST([MAC_ROBBER_LDFLAGS_SHARED])


AC_CONFIG_FILES([Makefile])
AC_OUTPUT
