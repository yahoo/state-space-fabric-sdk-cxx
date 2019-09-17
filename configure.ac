dnl This is a GNU -*- autoconf -*- specification that is processed by Autoconf.
dnl Copyright 2019, Oath Inc.
dnl Licensed under the terms of the Apache-2.0 license.
dnl See the LICENSE file in https://github.com/yahoo/hyperledger-fabric-sdk-c++/blob/master/LICENSE for terms.
dnl
dnl ./buildconf &&
dnl ./configure --prefix=/opt/hyperledger/fabric --with-std-tunitas=/opt/tunitas --with-std-scold=/opt/std/scold &&
dnl make &&
dnl make check &&
dnl make install &&
dnl echo OK DONE
dnl
AC_INIT([fabric-sdk-c++], [0.0.2], [state-space@verizonmedia.com])
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

#
# To perform production builds, only the WITH_STD mentions must be replicated in
#   Makefile.am: INSTALLATION_AREAS
#
# To perform development builds, the mentions herein must be replicated faithfully
#   Makefile.am: DEVLOPMENT_AREAS, TESTING_AREAS
#   Makefile.am: INSTALLATION_AREAS (same as before)
#

dnl Release 01 (Maximum Hammer) does not use this
TF_WITH_STD([hyperledger-fabric]) dnl You won't need this until Hyperledger Fabric delivers (we deliver) a C++ API (an "SDK")
TF_WITH_SUBSYSTEM([hyperledger-fabric-db], [], [The Hyperledger Fabric Data Base C++ Client-side SDK])
TF_WITH_SUBSYSTEM([hyperledger-fabric-ca], [], [The Hyperledger Fabric Certificate Authority C++ Client-side SDK])
TF_WITH_SUBSYSTEM([hyperledger-fabric], [], [The Hyperledger Fabric C++ Client-side SDK])
TF_WITH_SUBSYSTEM([hyperledger], [], [The Hyperledger C++ Client-side SDK])

TF_WITH_STD([tunitas])
TF_WITH_SUBSYSTEM([temerarious-flagship], [], [The Tunitas Build System])
TF_WITH_SUBSYSTEM([tunitas-basics], [], [The Tunitas Basics])

# And mention these in $(DEVELOPMENT_AREAS) in Makefile.am
TF_WITH_STD([scold]) dnl the core modules system
dnl NO ---> TF_WITH_MODULE([json]) <--- NO ----> NO DEPENDENCY ON module-json (there is no JSON in fabric)
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
