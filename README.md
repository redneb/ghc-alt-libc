# GHC compiled against alternative C standard libraries on Linux

This repository contains precompiled binary releases of [GHC](https://www.haskell.org/ghc/) (The Glasgow Haskell Compiler) for linux using [musl](http://www.musl-libc.org/) and [uClibc](http://www.uclibc.org/) instead of [glibc](https://www.gnu.org/software/libc/).

These are fully bootstrapped (i.e. stage 2) GHC binaries and *not cross compilers*. So they will not work in a typical glibc based linux distribution. You need a complete musl/uclibc based environment to use them. Also, the binaries produced by these compilers will all depend on musl/uclibc and not work on most glibc based distros. On the other hand, statically linked binaries should work everywhere.

## Downloads

See [releases](https://github.com/redneb/ghc-alt-libc/releases).

## How to use this

You need a complete musl/uClibc based environment. See [here](HOWTO-gentoo-musl-chroot.md) for an example using the experimental gentoo image based on musl.

## Notes

 * [Notes](NOTES-musl.md) for the musl release.
 * [Notes](NOTES-uClibc.md) for the uClibc release.
