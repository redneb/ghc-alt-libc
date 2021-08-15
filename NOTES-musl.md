# musl based binary releases of GHC

## Motivation

Static linking with glibc is problematic. On the other hand, static linking can simplify deployment and distribution of binaries. Unlike glibc, musl officially supports static linking and in fact it has been optimized for it.

## Known issues

None so for.

## Release notes

 * For 8.10.5/8.10.5: Compiled against `musl-1.2.1` and `linux-headers-5.10` on a gentoo system. Depends on `libgmp.so.10` and `libtinfow.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.10.3/8.10.4/9.0.1: Compiled against `musl-1.2.1` and `linux-headers-4.14` on a gentoo system. Depends on `libgmp.so.10` and `libtinfow.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.8.4/8.10.2: Compiled against `musl-1.1.24` and `linux-headers-4.14` on a gentoo system. Depends on `libgmp.so.10` and `libtinfow.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.8.2/8.8.3/8.10.1: Compiled against `musl-1.1.24` and `linux-headers-3.18` on a gentoo system. Depends on `libgmp.so.10` and `libtinfow.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.6.5/8.8.1: Compiled against `musl-1.1.21` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.4.4/8.6.2/8.6.3/8.6.4: Compiled against `musl-1.1.20` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.6.1: Compiled against `musl-1.1.20` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`. I used `gcc-7.3.0` to compile this. Gentoo's gcc now produces pie binaries by default. I wasn't able to make that work with ghc, so I had to pass the `-no-pie` flag everywhere, by using the following `build.mk`
 ```
V=1
HADDOCK_DOCS=NO
HSCOLOUR_SRCS=NO
BUILD_SPHINX_HTML=NO
BUILD_SPHINX_PDF=NO
BeConservative=YES
SRC_HC_OPTS+= -optc-no-pie -optl-no-pie
SRC_CC_OPTS+= -no-pie
SRC_LD_OPTS+= -no-pie
 ```
 * For 8.4.1/8.4.2/8.4.3: Compiled against `musl-1.1.19` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`. I used `gcc-6.4.0` to compile this. Gentoo's gcc now produces pie binaries by default. I wasn't able to make that work with ghc, so I had to pass the `-no-pie` flag everywhere, by using the following `build.mk`
 ```
V=1
HADDOCK_DOCS=NO
HSCOLOUR_SRCS=NO
BUILD_SPHINX_HTML=NO
BUILD_SPHINX_PDF=NO
BeConservative=YES
SRC_HC_OPTS+= -optc-no-pie -optl-no-pie
SRC_CC_OPTS+= -no-pie
SRC_LD_OPTS+= -no-pie
 ```
 * For 8.2.1: Compiled against `musl-1.1.16` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.6`. The `--disable-ld-override` flag was used to configure the sources. The same flag should probably be used for installation too, i.e. `./configure --disable-ld-override --prefix=...`.
 * For 8.0.2: Compiled against `musl-1.1.15` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.6`.
 * For 8.0.1: Compiled against `musl-1.1.14` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.10.3: Compiled against `musl-1.1.12` and `linux-headers-3.1` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.10.2: Compiled against `musl-1.1.10` and `linux-headers-3.1` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.10.1: Compiled against `musl-1.1.8` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.8.4: Compiled against `musl-1.1.8` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.6.3: Compiled against `musl-1.1.8` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.

## Patches used

 * For 7.10.x and above: *none*.
 * For 7.8.4: [fix-execvpe-signature-ghc-7.8.4.patch](patches/fix-execvpe-signature-ghc-7.8.4.patch).
 * For 7.6.3: [fix-execvpe-signature-ghc-7.6.3.patch](patches/fix-execvpe-signature-ghc-7.6.3.patch).
