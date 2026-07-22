## Process this file with automake to produce Makefile.in
# Makefile.am for volpack
# Andreas Tille <tille@debian.org> and Daniel Leidert <daniel.leidert@wgdd.de>
# GPL

SUBDIRS = doc man examples

EXTRA_DIST = vp_compA.m4 vp_warpA.m4 makeopts

CLEANFILES = $(COMP_SRCS) $(WARP_SRCS) vp_opts.c

ACLOCAL_AMFLAGS = -I m4
AM_CFLAGS = $(AC_FLAGS) $(CCOPT_FLAGS) $(MFLAGS) \
            $(PROTO_FLAG) $(UNROLL_FLAG) $(OPT_FLAGS)
AM_LDFLAGS = -version-info @LIBVOLPACK_VERSION_INFO@

# Make sure, the library and source files are built first.
BUILT_SOURCES = vp_opts.c $(COMP_SRCS) $(WARP_SRCS) $(lib_LTLIBRARIES)

lib_LTLIBRARIES  = libvolpack.la

dist_libvolpack_la_SOURCES = volpack.h vp_global.h patchlevel.h \
			vp_check.c vp_context.c vp_extract.c vp_file.c vp_linalg.c vp_octree.c \
		        vp_renderA.c vp_renderB.c vp_renderC.c vp_renderR.c vp_resample.c \
			vp_rle.c vp_shade.c vp_transpose.c vp_util.c vp_view.c vp_warp.c
nodist_libvolpack_la_SOURCES =  $(COMP_SRCS) $(WARP_SRCS)

# Public headers, copied to $(prefix)/include/
include_HEADERS = volpack.h

vp_opts.c: makeopts Makefile
	./makeopts vp_opts.c $(CFLAGS)

# list of optional C source files to build with code specialized                          
# for particular shaders and resampling filters                                           
OPT_SRCS = vp_compAC11B.c vp_compAC31B.c vp_compAC32B.c \
           vp_compAR11B.c vp_compAR31B.c vp_compAR32B.c

# C define flags corresponding to COMP_SRCS; these tell the dispatch
# routines in the library which object files are available
OPT_FLAGS = -DCOMP_AC11B   -DCOMP_AC31B   -DCOMP_AC32B \
            -DCOMP_AR11B   -DCOMP_AR31B   -DCOMP_AR32B

COMP_SRCS = vp_compAC1NB.c vp_compAC3NB.c vp_compAR1NB.c vp_compAR3NB.c \
            vp_compAC1PB.c vp_compAC3PB.c vp_compAR1PB.c vp_compAR3PB.c \
            vp_compAC00G.c vp_compAR00G.c vp_compAC1NS.c vp_compAC3NS.c \
            vp_compAR1NS.c vp_compAR3NS.c $(OPT_SRCS)

WARP_SRCS = vp_warpA101N.c vp_warpA301N.c vp_warpA110N.c vp_warpA111N.c \
            vp_warpA330N.c vp_warpA331N.c vp_warpA330R.c vp_warpA331R.c

COMP_IN = vp_compA.m4
WARP_IN = vp_warpA.m4

ESRC = vp_raycast.c
EOBJ = vp_raycast.o

$(COMP_SRCS): $(COMP_IN)
	$(M4) -DSourceFile=$@ $^ > $@

$(WARP_SRCS): $(WARP_IN)
	$(M4) -DSourceFile=$@ $^ > $@

MAINTAINERCLEANFILES = autom4te.cache
