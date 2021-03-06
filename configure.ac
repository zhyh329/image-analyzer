#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.61)
AC_INIT([image-analyzer], [dev], [jdegges@gmail.com])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_CONFIG_SRCDIR([config.h.in])
AC_CONFIG_HEADER([config.h])

# Checks for programs.
AC_CANONICAL_HOST
AC_CANONICAL_BUILD
AC_PROG_CC

# Checks for libraries.
AC_ARG_WITH([sdl],
    [AS_HELP_STRING([--with-sdl],
        [use SDL to optionally display output @<:@default=check@:>@])],
    [],
    [with_sdl=check])
AC_ARG_WITH([opencv],
    [AS_HELP_STRING([--with-opencv],
        [include opencv library functions which some filters depend on @<:@default=check@:>@])],
    [],
    [with_opencv=check])
AC_ARG_WITH([ffmpeg],
    [AS_HELP_STRING([--with-ffmpeg],
        [adds video input support using ffmpeg and swscale libraries @<:@default=check@:>@])],
    [],
    [with_ffmpeg=check])
AC_ARG_WITH([v4l],
    [AS_HELP_STRING([--width-v4l],
        [allows capture from v4l compliant cameras @<:@default=check@:>@])],
    [],
    [with_v4l=check])
AC_ARG_WITH([v4l2],
    [AS_HELP_STRING([--with-v4l2],
        [allows capture from v4l2 compliant cameras @<:@default=check@:>@])],
    [],
    [with_v4l2=check])

AC_CHECK_LIB([freeimage], [main])
AC_CHECK_LIB([stdc++], [main])
AC_CHECK_LIB([pthread], [main])
AS_IF([test "x$with_sdl" != xno],
    [AC_HAVE_LIBRARY([-lSDL])])
AS_IF([test "x$with_opencv" != xno],
    [AC_HAVE_LIBRARY([cxcore]) AC_HAVE_LIBRARY([cv]) AC_HAVE_LIBRARY([highgui]) AC_HAVE_LIBRARY([cvaux]) AC_HAVE_LIBRARY([ml])])
AS_IF([test "x$with_ffmpeg" != xno],
    [AC_CHECK_LIB([avutil], [main])
     AC_CHECK_LIB([avformat], [main])
     AC_CHECK_LIB([avcodec], [main])
     AC_CHECK_LIB([z], [main])
     AC_CHECK_LIB([swscale], [main])])

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([fcntl.h inttypes.h limits.h malloc.h stdint.h stdlib.h string.h sys/ioctl.h sys/time.h unistd.h])
AC_CHECK_HEADERS([FreeImage.h])
AC_CHECK_HEADERS([pthread.h])
AS_IF([test "x$with_sdl" != xno],
    [AC_CHECK_HEADERS([SDL/SDL.h])])
AS_IF([test "x$with_opencv" != xno],
    [AC_CHECK_HEADERS([opencv/cv.h opencv/highgui.h opencv/cv.h opencv/cxcore.h])])
AS_IF([test "x$with_ffmpeg" != xno],
    [AC_CHECK_HEADERS([libavcodec/avcodec.h libavformat/avformat.h libswscale/swscale.h])])
AS_IF([test "x$with_v4l" != xno],
    [AC_CHECK_HEADERS([linux/videodev.h])])
AS_IF([test "x$with_v4l2" != xno],
    [AC_CHECK_HEADERS([linux/videodev2.h])])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_CONST
AC_C_INLINE
AC_TYPE_INT32_T
AC_TYPE_INT8_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_HEADER_TIME
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_PROG_GCC_TRADITIONAL
AC_FUNC_MALLOC
AC_FUNC_MMAP
AC_FUNC_SELECT_ARGTYPES
AC_FUNC_STAT
AC_CHECK_FUNCS([gettimeofday memset munmap pow regcomp select sqrt strcasecmp strerror strrchr strtoul])

AC_CONFIG_FILES([Makefile
                 src/Makefile])
AC_OUTPUT
