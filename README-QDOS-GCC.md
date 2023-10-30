# QDOS-GCC Cross Compiling tips

## MacOS

1. Download compiled binaries

    C68 compiler - built on more recet toolset/gcc
    https://github.com/stronnag/xtc68/releases

    Extract in your home
    ```sh
    cd $HOME
    tar zxf xtc68-2022-09-01-macos-amd64.tar.gz
    ```

1. Install MacOS tooling

    ```sh
    brew install autoconf automake libtool
    ```

1. expand your env

    ```sh
    export PATH=~/xtc68/bin:$PATH
    ```

1. run autoreconf

1. Compile
    Remember to extend `--libs` with `-I ~/xtc68/share/qdos/include/`


# MacOS example

- autoreconf

```
user@macos [ ~/QL/snake ] $ autoreconf -i
glibtoolize: putting auxiliary files in '.'.
glibtoolize: copying file './ltmain.sh'
glibtoolize: Consider adding 'AC_CONFIG_MACRO_DIRS([m4])' to configure.ac,
glibtoolize: and rerunning glibtoolize and aclocal.
glibtoolize: Consider adding '-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
configure.ac:17: warning: The macro `AC_HEADER_STDC' is obsolete.
configure.ac:17: You should run autoupdate.
./lib/autoconf/headers.m4:704: AC_HEADER_STDC is expanded from...
configure.ac:17: the top level
configure.ac:24: warning: The macro `AC_HEADER_TIME' is obsolete.
configure.ac:24: You should run autoupdate.
./lib/autoconf/headers.m4:743: AC_HEADER_TIME is expanded from...
configure.ac:24: the top level
configure.ac:30: warning: The macro `AC_TYPE_SIGNAL' is obsolete.
configure.ac:30: You should run autoupdate.
./lib/autoconf/types.m4:776: AC_TYPE_SIGNAL is expanded from...
configure.ac:30: the top level
configure.ac:32: warning: The macro `AC_PROG_LIBTOOL' is obsolete.
configure.ac:32: You should run autoupdate.
aclocal.m4:122: AC_PROG_LIBTOOL is expanded from...
configure.ac:32: the top level
configure.ac:11: installing './compile'
configure.ac:31: installing './config.guess'
configure.ac:31: installing './config.sub'
configure.ac:6: installing './install-sh'
configure.ac:6: installing './missing'
Makefile.am: installing './depcomp'

```

- configure

```
user@macos [ ~/QL/snake ] $ ./configure
checking for a BSD-compatible install... /usr/local/bin/ginstall -c
checking whether build environment is sane... yes
checking for a race-free mkdir -p... /usr/local/bin/gmkdir -p
checking for gawk... no
checking for mawk... no
checking for nawk... no
checking for awk... awk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether the compiler supports GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to enable C11 features... none needed
checking whether gcc understands -c and -o together... yes
checking whether make supports the include directive... yes (GNU style)
checking dependency style of gcc... gcc3
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for stdio.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for strings.h... yes
checking for sys/stat.h... yes
checking for sys/types.h... yes
checking for unistd.h... yes
checking for sys/time.h... yes
checking for sys/select.h... yes
checking for sys/socket.h... yes
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for stdio.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for stdint.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether closedir returns void... no
checking for working memcmp... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking build system type... x86_64-apple-darwin22.6.0
checking host system type... x86_64-apple-darwin22.6.0
checking whether lstat correctly handles trailing slash... no
checking whether stat accepts an empty string... no
checking how to print strings... printf
checking for a sed that does not truncate output... /usr/bin/sed
checking for fgrep... /usr/bin/grep -F
checking for ld used by gcc... /Library/Developer/CommandLineTools/usr/bin/ld
checking if the linker (/Library/Developer/CommandLineTools/usr/bin/ld) is GNU ld... no
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 786432
checking how to convert x86_64-apple-darwin22.6.0 file names to x86_64-apple-darwin22.6.0 format... func_convert_file_noop
checking how to convert x86_64-apple-darwin22.6.0 file names to toolchain format... func_convert_file_noop
checking for /Library/Developer/CommandLineTools/usr/bin/ld option to reload object files... -r
checking for file... file
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... no
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... no
checking if : is a manifest tool... no
checking for dsymutil... dsymutil
checking for nmedit... nmedit
checking for lipo... lipo
checking for otool... otool
checking for otool64... no
checking for -single_module linker flag... ld: warning: -single_module is obsolete
no
checking for -exported_symbols_list linker flag... yes
checking for -force_load linker flag... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking for gcc option to produce PIC... -fno-common -DPIC
checking if gcc PIC flag -fno-common -DPIC works... yes
checking if gcc static flag -static works... no
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/Library/Developer/CommandLineTools/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... darwin22.6.0 dyld
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for memset... yes
configure: compile for general Unix with ncurse lib
checking for initscr in -lncurses... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
```

- make

```
user@macos [ ~/QL/snake ] $ make -I ~/xtc68/share/qdos/include/
/Library/Developer/CommandLineTools/usr/bin/make  all-am
gcc -DHAVE_CONFIG_H -I.  -Wall   -g -O2 -MT snake.o -MD -MP -MF .deps/snake.Tpo -c -o snake.o snake.c
mv -f .deps/snake.Tpo .deps/snake.Po
gcc -DHAVE_CONFIG_H -I.  -Wall   -g -O2 -MT queue.o -MD -MP -MF .deps/queue.Tpo -c -o queue.o queue.c
mv -f .deps/queue.Tpo .deps/queue.Po
gcc -DHAVE_CONFIG_H -I.  -Wall   -g -O2 -MT osal.o -MD -MP -MF .deps/osal.Tpo -c -o osal.o osal.c
mv -f .deps/osal.Tpo .deps/osal.Po
gcc -DHAVE_CONFIG_H -I.  -Wall   -g -O2 -MT log.o -MD -MP -MF .deps/log.Tpo -c -o log.o log.c
mv -f .deps/log.Tpo .deps/log.Po
/bin/sh ./libtool  --tag=CC   --mode=link gcc  -g -O2   -o snake snake.o queue.o osal.o log.o  -lncurses
libtool: link: gcc -g -O2 -o snake snake.o queue.o osal.o log.o  -lncurses
```

