%AC_COPYRIGHT([
 Copyright (c) Her Majesty the Queen in right of Canada  (2014)
 All rights reserved.

 Redistribution and use in source and binary forms, with or without
 modification, are permitted provided that the following conditions
 are met:
 
 * Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.
 * Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in
   the documentation and/or other materials provided with the
   distribution.
 * Neither the name of Her Majesty the Queen in right of Canada nor
   the names of her contributors may be used to endorse or promote
   products derived from this software without specific prior written
   permission.
 
 THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
 "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
 LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
 FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE
 COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
 INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
 BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
 LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
 CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
 LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN
 ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
 POSSIBILITY OF SUCH DAMAGE.

 See toplevel COPYING for more information.
])

AC_INIT([emane-model-crc-tdma],0.0.1,[jiangxin dot hu at crc dot gc dot ca])

AC_CONFIG_SRCDIR([src])

AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([1.9.6])

AC_PROG_CXX

AC_PROG_CXXCPP

AX_CXX_COMPILE_STDCXX_11([noext],[mandatory])

AC_PROG_INSTALL

AC_LIBTOOL_WIN32_DLL
AC_PROG_LIBTOOL

AC_LANG([C++])

AC_ARG_WITH(profile,
           [  --with-profile          add profiling support (off)])

AC_ARG_WITH(debug,
           [  --with-debug            add debug support (off)])

AC_ARG_WITH(dot,
           [  --with-dot              Use dot with doxygen (off)])

AC_ARG_WITH([verbose-logging],
           [  --without-verbose-logging  disable verbose logging support (on)],
           [],
           [with_verbose_logging=yes])


AC_ARG_WITH([testcases],
           [  --with-testcases        add testcases to build (off)],
           [AM_CONDITIONAL(WITH_TESTCASES,true)],
           [AM_CONDITIONAL(WITH_TESTCASES,false)])

PKG_CHECK_MODULES([libxml2], libxml-2.0)
PKG_CHECK_MODULES([libemane], libemane)
PKG_CHECK_MODULES([libuuid], uuid)

LDFLAGS="$LDFLAGS -lpthread -ldl"

AC_C_BIGENDIAN(AC_DEFINE([__BYTE_ORDER],__BIG_ENDIAN,[Big Endian]),
AC_DEFINE([__BYTE_ORDER],__LITTLE_ENDIAN,[Little Endian]))
AC_DEFINE([__LITTLE_ENDIAN],1234,[for the places where it is not defined])
AC_DEFINE([__BIG_ENDIAN],4321,[for the places where it is not defined])

# compiler options
CXXFLAGS="$CXXFLAGS -W -Wall -g0 -O3"

# options for use with gprof
if test "$with_profile" = "yes"
then
CPPFLAGS="$CPPFLAGS -g -pg"
LDFLAGS="$LDFLAGS -g -pg"
fi

# options for use with debug
if test "$with_debug" = "yes"
then
CPPFLAGS="$CPPFLAGS -g -O0"
LDFLAGS="$LDFLAGS -g -O0"
fi

# options for use with verbose logging
if test "$with_verbose_logging" = "yes"
then
CPPFLAGS="$CPPFLAGS -DVERBOSE_LOGGING"
fi

LANG=C
AC_SUBST(LANG)

AC_OUTPUT(
 Makefile
 src/Makefile
)
