## Process this file with automake to produce Makefile.in
# Makefile.am for volpack/examples
# Andreas Tille <tille@debian.org> and Daniel Leidert <daniel.leidert@wgdd.de>
# GPL

EXTRA_DIST = brainsmall.den check.ppm README test.csh

CLEANFILES = $(EXAMPLEOUTPUT)

AM_CPPFLAGS = -I$(top_srcdir)
LDADD = $(top_builddir)/libvolpack.la @LIBS@

noinst_PROGRAMS = classifyvolume makeoctree makevolume rendervolume scalevolume

classifyvolume_SOURCES = classifyvolume.c volume.h
makeoctree_SOURCES     = makeoctree.c volume.h
makevolume_SOURCES     = makevolume.c volume.h
rendervolume_SOURCES   = rendervolume.c volume.h
scalevolume_SOURCES    = scalevolume.c denfile.c

# In case there are some remainings from the example tests:
EXAMPLEOUTPUT = brainsmall.cv brainsmall.oct brainsmall*.ppm brainsmall.rv


