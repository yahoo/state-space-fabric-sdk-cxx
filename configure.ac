dnl -*- autoconf -*-
dnl Copyright (c) 2019 Verizon Media, Inc.  See the LICENSE statement nearby.
dnl
dnl ./buildconf &&
dnl ./configure --prefix=/opt/hyperledger/fabric --with-std-tunitas=/opt/tunitas --with-std-scold=/opt/std/scold &&
dnl make &&
dnl make check &&
dnl make install &&
dnl echo OK DONE
dnl
AC_INIT([fabric-sdk-c++], [0.0.0], [/dev/null@verizonmedia.com])
TF_INIT(AC_PACKAGE_NAME, AC_PACKAGE_VERSION, AC_PACKAGE_BUGREPORT)

dnl These options are also in the Makefile.am in AUTOMAKE_OPTIONS
dnl AM_INIT_AUTOMAKE([no-define subdir-objects foreign])
AM_SILENT_RULES([yes])

AC_CONFIG_SRCDIR([src/hyperledger/fabric/namespace.xcpp])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile])

#
# To have submodules
#   configure.ac: TF_CONFIG_SUBMODULES([submodules], [...list...])
#   Makefile.am:  SUBDIRS = @subdirs@
# to have no submodules
#   comment these schemes out in both places
#

TF_COMPONENT_METADIRECTORY_TIERS
TF_ENABLE_GNU
TF_ENABLE_GDB
TF_ENABLE_GCC
TF_ENABLE_MOCK_BUILD

TF_WITH_STD([scold]) dnl the core modules system
TF_WITH_STD([tunitas]) dnl application data types
TF_WITH_STD([hyperledger-fabric]) dnl this is us, we are the Hyperledger Fabric C++ API

TF_WITH_SUBSYSTEM([temerarious-flagship], [], [The Tunitas Build System])
TF_WITH_SUBSYSTEM([tunitas-basics], [], [The Tunitas Basics])

# And mention these in $(DEVELOPMENT_AREAS) in Makefile.am
dnl NO DEPENDENCY ON JSON ---> TF_WITH_MODULE([json]) <--- NO DEPENDENCY ON JSON
TF_WITH_MODULE([nonstd])
TF_WITH_MODULE([posix])
TF_WITH_MODULE([std])
TF_WITH_MODULE([string]) dnl a.k.a. c-string
TF_WITH_MODULE([sys])

TF_WITH_MODULE([cppunit])
TF_WITH_MODULE([rigging]) dnl a.k.a. unit-rigging -> rigging-unit

TF_MSG_VERBOSE([compiler-specific (alphabetical)])
TF_WITH_NONSTD([cppunit])
TF_WITH_NONSTD([gcc]) dnl but modern gcc-8.2.0 & beyond is fine
TF_WITH_USR_LOCAL

AM_PROG_AR
LT_PREREQ([2.4.2])
LT_INIT
AC_PROG_CC
AC_PROG_CXX
AM_PROG_CC_C_O
TF_PROG_DC
TF_CHECK_CPPUNIT
TF_WITH_USR_LOCAL

TF_CHECK_STD_FILESYSTEM dnl get @libstd_filesystem@ for Makefile.am

TF_FINALIZE
