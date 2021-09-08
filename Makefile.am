# This is a GNU -*- Makefile -*- fragment that is included by Automake
# Copyright Yahoo Inc. 2021.
# Licensed under the terms of the Apache-2.0 license.
# See the LICENSE file in https://github.com/yahoo/hyperledger-fabric-sdk-c++/blob/master/LICENSE for terms.

# [[FIXTHIS]] - ACLOCAL_AMFLAGS is evaluated by automake *before* make even runs
# It uses /bin/bash eval to evaluate the line ...
#    so make variables $(...) look like backticks
#    but make variables ${...} look like shell variables with defaults
#
# is a subshell
#    /usr/bin/libtoolize: line 3772: temerarious_flagship_datadir: command not found
#
# these must all be on a single line, no backslash continuations
#ACLOCAL_AMFLAGS = -I m4 -I ${temerarious_flagship_datadir:-/opt/tunitas/share/temerarious-flagship}/ac -I ${hypogeal_twilight_datadir:-/opt/scold/share/hypogeal-twilight}/m4
ACLOCAL_AMFLAGS = -I m4
AUTOMAKE_OPTIONS = no-define subdir-objects foreign

default:
# also configure.ac and TF_SUBMODULE_CONFIGURE
# SUBDIRS = @subdirs@
include @temerarious_flagship_datadir@/am/build.am

# These match with TF_WITH_MODULE in configure.ac
# You do not need them unless you are doing co-development of these packages *with* PrivacyChain SDK C++
DEVELOPMENT_AREAS = \
  $(module_langu_prefix) \
  $(module_nonstd_prefix) \
  $(module_posix_prefix) \
  $(module_shell_prefix) \
  $(module_std_prefix) \
  $(module_string_prefix) \
  $(module_sys_prefix) \
  $(tunitas_basics_prefix) \
  $(end)
TESTING_AREAS = \
  $(module_cppunit_prefix) \
  $(module_rigging_prefix) \
  $(end)
INSTALLATION_AREAS = \
  $(nonstd_cppunit_prefix) \
  $(nonstd_gcc_prefix) \
  $(std_scold_prefix) \
  $(std_tunitas_prefix) \
  $(end)

include src/hyperledger/fabric/Makefrag.am
include src/tests/unit/Makefrag.am
include src/want/Makefrag.am

INSTALL_MODULES = \
  $(lib_libhyperledger_fabric_la_MODULES) \
  $(lib_libwant_la_MODULES) \
  $(end)

bin_PROGRAMS = $(none)
sbin_PROGRAMS = $(none)
lib_LTLIBRARIES = \
  $(lib_libhyperledger_fabric_la) \
  $(end)
noinst_LTLIBRARIES = \
  $(lib_libwant_la) \
  $(end)
check_PROGRAMS = \
  $(check_bin_unit) \
  $(end)

include tests/unit/Makefrag.am
XFAIL_TESTS = \
  $(tests_unit_XFAIL_TESTS) \
  $(end)
TESTS = \
  $(tests_unit_TESTS) \
  $(end)

SEARCHPATH = $(SEARCHPATH_SCOLD_MODULES)
LOADPATH   = $(LOADPATHPATH_SCOLD_MODULES)

# --- Mostly boilerplate beyond here
#
# -Wall      ... the language isn't complete without it
# -std=c++20 ... and more is required
# -ggdb      ... and recall that -ggdb and -O2 don't play well together

Makefile_COMPILER_CPPFLAGS_SET = @CPPFLAGS_gcc@ @CPPFLAGS_gdb@
Makefile_COMPILER_CFLAGS_SET   =   @CFLAGS_gcc@   @CFLAGS_gdb@
Makefile_COMPILER_CXXFLAGS_SET = @CXXFLAGS_gcc@ @CXXFLAGS_gdb@
Makefile_COMPILER_LDFLAGS_SET  =  @LDFLAGS_gcc@  @LDFLAGS_gdb@ @libstd_filesystem@

Makefile_nonstd_PACKAGE_CPPFLAGS_SET = @usr_local_CPPFLAGS@
Makefile_nonstd_PACKAGE_CFLAGS_SET   =   @usr_local_CFLAGS@
Makefile_nonstd_PACKAGE_CXXFLAGS_SET = @usr_local_CXXFLAGS@
Makefile_nonstd_PACKAGE_LDFLAGS_SET  =  @usr_local_LDFLAGS@

# n.b. there is no JSON at the Hyperledger Fabric API level.
Makefile_PACKAGE_CPPFLAGS_SET = 
Makefile_PACKAGE_CFLAGS_SET   = 
Makefile_PACKAGE_CXXFLAGS_SET = 
Makefile_PACKAGE_LDFLAGS_SET  = 

Makefile_nonstd_CHECK_CPPFLAGS_SET = 
Makefile_nonstd_CHECK_CFLAGS_SET   = 
Makefile_nonstd_CHECK_CXXFLAGS_SET = 
Makefile_nonstd_CHECK_LDFLAGS_SET  = 

Makefile_CHECK_CPPFLAGS_SET = @CPPFLAGS_cppunit@ @CPPFLAGS_no_install@
Makefile_CHECK_CFLAGS_SET   =   @CFLAGS_cppunit@   @CFLAGS_no_install@
Makefile_CHECK_CXXFLAGS_SET = @CXXFLAGS_cppunit@ @CXXFLAGS_no_install@
Makefile_CHECK_LDFLAGS_SET  =  @LDFLAGS_cppunit@  @LDFLAGS_no_install@

# The PACKAGE_, CHECK_ and AND_CHECK_ prefixed-variables are aggregated in .../mk/toolflags.mk in temerarious-flagship (hypogeal-twilight >= 0.45)
AM_CPPFLAGS = $(PACKAGE_CPPFLAGS_SET)
AM_CFLAGS   = $(PACKAGE_CFLAGS_SET)
AM_CXXFLAGS = $(PACKAGE_CXXFLAGS_SET)
AM_LDFLAGS  = $(V_LDFLAGS_avoid.VERBOSE_Veq$(V))
AM_LIBTOOLFLAGS = $(V_LIBTOOLFLAGS_VERBOSE_Veq$(V))

default: all

.PHONY: clean-local mostlyclean-local distclean-local
clean-local mostlyclean-local distclean-local::
clean-dependencies::
clean-local:: clean-dependencies

