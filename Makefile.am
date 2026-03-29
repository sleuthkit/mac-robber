ACLOCAL_AMFLAGS = -I m4
bin_PROGRAMS = mac-robber
EXTRA_DIST = .indent.pro CHANGES
DISTCLEANFILES  = *~ core.* *core
mac_robber_SOURCES = mac-robber.c

if DEBUG
AM_CFLAGS = $(MAC_ROBBER_CFLAGS_DEBUG)
mac_robber_CFLAGS = $(MAC_ROBBER_CFLAGS_DEBUG) 
else
mac_robber_CFLAGS = $(MAC_ROBBER_CFLAGS) 
endif

mac_robber_CPPFLAGS = $(MAC_ROBBER_CPPFLAGS)

if SHARED
mac_robber_LDFLAGS = $(MAC_ROBBER_LDFLAGS_SHARED)
else
mac_robber_LDFLAGS = $(MAC_ROBBER_LDFLAGS_STATIC)
endif


clean-local:
	rm -f core.* *core

indent:
	indent *.c

