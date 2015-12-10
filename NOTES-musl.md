# musl based binary releases of GHC

## Motivation

Static linking with glibc is problematic. On the other hand, static linking can simplify deployment and distribution of binaries. Unlike glibc, musl officially supports static linking and in fact it has been optimized for it.

## Known issues

None so for.

## Release notes

 * For 7.10.3: Compiled against `musl-1.1.12` and `linux-headers-3.1` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.10.2: Compiled against `musl-1.1.10` and `linux-headers-3.1` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.10.1: Compiled against `musl-1.1.8` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.8.4: Compiled against `musl-1.1.8` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.6.3: Compiled against `musl-1.1.8` and `linux-headers-3.16` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.

## Patches used

 * For 7.10.x: *none*.
 * For 7.8.4: [fix-execvpe-signature-ghc-7.8.4.patch](patches/fix-execvpe-signature-ghc-7.8.4.patch).
 * For 7.6.3: [fix-execvpe-signature-ghc-7.6.3.patch](patches/fix-execvpe-signature-ghc-7.6.3.patch).
