# This is a GNU -*- Makefile -*- fragment that is included by Automake
# Copyright Verizon Media.
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
  $(module_format_prefix) \
  $(module_json_prefix) \
  $(module_nonstd_prefix) \
  $(module_openssl_prefix) \
  $(module_posix_prefix) \
  $(module_shell_prefix) \
  $(module_slurp_prefix) \
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

default: all

devel: all-devel
devel-all: all-devel
devel-check: check-devel
all-devel check-devel : CPPFLAGS+=-Wno-cpp -Wno-deprecated-declarations
all-devel check-devel : CXXFLAGS+=-ggdb -O0
all-devel : all
check-devel : check

module_SOURCE_SET = \
  $(lib_libhyperledger_la_SOURCES) \
  $(lib_libhyperledger_crypto_la_SOURCES) \
  $(lib_libhyperledger_fabric_la_SOURCES) \
  $(lib_libhyperledger_fabric_ca_la_SOURCES) \
  $(lib_libhyperledger_fabric_utility_la_SOURCES) \
  $(lib_libwant_la_SOURCES) \
  $(end)

# these have to be installed in the C area, and installed the "C way"
nobase_include_HEADERS = \
  $(lib_libhyperledger_protos_la_HEADER_SET) \
  $(end)

.PHONY: clean-local mostlyclean-local distclean-local
clean-local mostlyclean-local distclean-local::
clean-dependencies::
clean-local:: clean-dependencies

# Hyperledger
include src/hyperledger/Makefrag.am
include src/hyperledger/crypto/Makefrag.am
include src/hyperledger/http/Makefrag.am
include src/hyperledger/json/Makefrag.am
include src/hyperledger/pki/Makefrag.am
include src/hyperledger/protos/Makefrag.am
# Hyperledger Fabric
include src/hyperledger/fabric/Makefrag.am
$(info ADDTHIS ---> include src/hyperledger/fabric/utility/Makefrag.am)
include src/hyperledger/fabric/user/Makefrag.am
include src/hyperledger/fabric/v0/Makefrag.am
# Hyperledger Fabric CA (Certificate Authority)
include src/hyperledger/fabric/ca/Makefrag.am
include src/hyperledger/fabric/ca/protocol/Makefrag.am
# addenda
include src/langu/Makefrag.am
include src/nonstd/Makefrag.am
include src/shell/Makefrag.am
include src/std/Makefrag.am
include src/want/Makefrag.am
# test rigging
include src/rigging/hyperledger/Makefrag.am
include src/tests/concepts/Makefrag.am
include src/tests/Makefrag.am
include src/tests/unit/Makefrag.am
include src/tests/crypto/Makefrag.am
include src/tests/pki/Makefrag.am
include src/tests/decode/Makefrag.am
include src/tests/encode/Makefrag.am
include src/tests/want/Makefrag.am
include src/tests/nonstd/Makefrag.am
include src/tests/langu/Makefrag.am
include src/tests/shell/Makefrag.am # [[deprecating]] intead use namespace ::shell or its successors

$(lib_libhyperledger_la_OBJECTS): $(lib_libhyperledger_protos_la_SOURCES)

bin_PROGRAMS = $(none)
sbin_PROGRAMS = $(none)
lib_LTLIBRARIES = \
  $(lib_libhyperledger_la) \
  $(lib_libhyperledger_fabric_la) \
  $(lib_libhyperledger_fabric_ca_la) \
  $(lib_libhyperledger_fabric_user_la) \
  $(end)
noinst_LTLIBRARIES = \
  $(lib_libhyperledger_crypto_la) \
  $(lib_libhyperledger_http_la) \
  $(lib_libhyperledger_json_la) \
  $(lib_libhyperledger_pki_la) \
  $(lib_libhyperledger_protos_la) \
  $(lib_libhyperledger_fabric_utility_la) \
  $(lib_libhyperledger_fabric_v0_la) \
  $(lib_libhyperledger_fabric_ca_protocol_la) \
  $(lib_libstd_la) \
  $(lib_libwant_langu_la) \
  $(lib_libwant_nonstd_la) \
  $(lib_libwant_shell_la) \
  $(lib_libwant_la) \
  $(end)
check_PROGRAMS = \
  $(check_bin_unit) \
  $(check_bin_unit_crypto) \
  $(check_bin_unit_pki) \
  $(check_bin_decode) \
  $(check_bin_encode) \
  $(check_bin_want) \
  $(check_bin_nonstd) \
  $(check_bin_langu) \
  $(check_bin_shell) \
  $(end)
check_LTLIBRARIES = \
  $(check_lib_librigging_hyperledger_la) \
  $(check_lib_libtests_concepts_la) \
  $(check_lib_libtests_la) \
  $(end)

include tests/unit/Makefrag.am
XFAIL_TESTS = \
  $(tests_unit_XFAIL_TESTS) \
  tests/crypto/all.test \
  $(end)
TESTS = \
  $(tests_unit_TESTS) \
  tests/decode/all.test \
  tests/encode/all.test \
  tests/crypto/all.test \
  tests/pki/all.test \
  tests/want/all.test \
  tests/nonstd/all.test \
  tests/langu/all.test \
  tests/shell/all.test \
  $(end)

# --- Mostly boilerplate beyond here
#
# -Wall      ... the language isn't complete without it
# -std=c++1y ... avoid
# -std=c++14 ... avoid
# -std=c++1z ... avoid
# -std=c++17 ... C++17
# -std=c++2a ... C++20 approximately
# -std=c++20 ... C++20
# -std=c++2b ... as close to C++23 (and beyond) as we can get
# -ggdb      ... and recall that -ggdb and -O2 don't play well together

Makefile_COMPILER_CPPFLAGS_SET =
Makefile_COMPILER_CFLAGS_SET   = -Wall @CFLAGS_gcc@   @CFLAGS_gdb@
Makefile_COMPILER_CXXFLAGS_SET = -Wall @CXXFLAGS_gcc@ @CXXFLAGS_gdb@
Makefile_COMPILER_LDFLAGS_SET  = -Wall @LDFLAGS_gcc@  @LDFLAGS_gdb@ @libstd_filesystem@

Makefile_nonstd_PACKAGE_CPPFLAGS_SET = @usr_local_CPPFLAGS@
Makefile_nonstd_PACKAGE_CFLAGS_SET   = @usr_local_CFLAGS@
Makefile_nonstd_PACKAGE_CXXFLAGS_SET = @usr_local_CXXFLAGS@
Makefile_nonstd_PACKAGE_LDFLAGS_SET  = @usr_local_LDFLAGS@

# n.b. there is no JSON at the Hyperledger Fabric API level.
Makefile_PACKAGE_CPPFLAGS_SET = 
Makefile_PACKAGE_CFLAGS_SET   = 
Makefile_PACKAGE_CXXFLAGS_SET = 
Makefile_PACKAGE_LDFLAGS_SET  = 

Makefile_nonstd_CHECK_CPPFLAGS_SET = 
Makefile_nonstd_CHECK_CFLAGS_SET   = 
Makefile_nonstd_CHECK_CXXFLAGS_SET = 
Makefile_nonstd_CHECK_LDFLAGS_SET  = 

Makefile_CHECK_CPPFLAGS_SET = @CPPFLAGS_cppunit@
Makefile_CHECK_CFLAGS_SET   = @CFLAGS_cppunit@
# compile all the test rigging without any optimization so we can see
Makefile_CHECK_CXXFLAGS_SET = @CXXFLAGS_cppunit@ -ggdb -O0
# see -no-install in https://www.gnu.org/software/libtool/manual/html_node/Link-mode.html
Makefile_CHECK_LDFLAGS_SET  = @LDFLAGS_cppunit@ -no-install $(REMOVEWHEN temerariouc-flagship provides this in an @-variable)

# See $(temerarious_flagship_prefix)/ac/toolflags.mk
# The following variable conjugations are provided in toolflags.mk
#
# For TOOL in { CPP C CXX LD }
#     PACKAGE_${TOOL}FLAGS_SET
#     CHECK_${TOOL+FLAGS_SET
#     AND_CHECK_${TOOL}FLAGS_SET
#
AM_CPPFLAGS = $(PACKAGE_CPPFLAGS_SET)
AM_CFLAGS   = $(PACKAGE_CFLAGS_SET)
AM_CXXFLAGS = $(PACKAGE_CXXFLAGS_SET)
AM_LDFLAGS  = $(V_LDFLAGS_avoid.VERBOSE_Veq$(V)) # Reminder: autotools does not put $(AM_LDFLAGS) anywhere it needs to be
AM_LIBTOOLFLAGS = $(V_LIBTOOLFLAGS_VERBOSE_Veq$(V))

# end
