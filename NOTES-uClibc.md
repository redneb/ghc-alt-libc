# uClibc based binary releases of GHC

## Known issues

 * All versions: compiling with `-dynamic` does not work, the resulting binaries will not be able to find GHC's `*.so` files. Similarly, GHC cannot be compiled with `DYNAMIC_GHC_PROGRAMS = YES` which is the default for `>=7.8`.
 * All versions: static liking with `-optl-static` does not work, the resulting binaries segfault.

## Release notes

 * For 7.10.1: Compiled against `uclibc-0.9.33.2` and `linux-headers-3.18` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.8.4: Compiled against `uclibc-0.9.33.2` and `linux-headers-3.18` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.
 * For 7.6.3: Compiled against `uclibc-0.9.33.2` and `linux-headers-3.18` on a gentoo system. Depends on `libgmp.so.10` and `libncursesw.so.5`.

## Patches used

 * For 7.10.1: [missing-eventfd_write.patch](patches/missing-eventfd_write.patch).
 * For 7.8.4: [missing-eventfd_write.patch](patches/missing-eventfd_write.patch).
 * For 7.6.3: *none*.
