# musl based binary releases of GHC

## Motivation

Static linking with glibc is problematic. On the other hand, static linking can simplify deployment and distribution of binaries. Unlike glibc, musl officially supports static linking and in fact it has been optimized for it.

## Known issues

None so for.

## Release notes

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
