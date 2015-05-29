Here's a quick and dirty way to set up a musl based chroot environment 
using the experimental gentoo image for x86_64:

    CHROOT_PATH=/var/tmp/gentoo-musl
    IMAGE_URI=http://distfiles.gentoo.org/experimental/amd64/musl/stage3-amd64-musl-vanilla-XXXXXX.tar.bz2
    GHC_URI=https://github.com/redneb/ghc-alt-libc/releases/download/XXX/ghc-YYY

    # setup the chroot environment:
    mkdir "$CHROOT_PATH"
    cd /var/tmp
    wget "$IMAGE_URI"
    tar xjf stage3-*-musl-vanilla-*.tar.bz2 -C "$CHROOT_PATH"
    wget "$GHC_URI"
    mv ghc-*-linux-musl.tar.xz "$CHROOT_PATH/var/tmp"

    # enter the chroot environment:
    for x in dev proc sys; do mount --bind /$x "$CHROOT_PATH/$x"; done
    cp -L /etc/resolv.conf "$CHROOT_PATH/etc"
    chroot "$CHROOT_PATH" /bin/bash -l
    PS1="(chroot) $PS1"

    # fetch the gentoo package db for the first time (slow):
    emerge-webrsync

    # enable static libraries (*.a), which are disabled by default:
    sed -ie 's/USE="/USE="static-libs /' /etc/portage/make.conf
    # reinstall/recompile gmp so that its static libs are available:
    emerge --oneshot dev-libs/gmp

    # install ghc:
    tar xJf /var/tmp/ghc-*-linux-musl.tar.xz -C /tmp
    cd /tmp/ghc-*;
    ./configure --prefix=/opt/ghc; make install
    
    # compile a hello world:
    cd /tmp
    echo 'main = putStrLn "Hello world"' > test.hs
    /opt/ghc/bin/ghc --make -O -optl-static test.hs
    ./test
    file ./test

Of course, using chroot like that is insecure, don't use it to install 
packages from hackage. A similar process can be used with LXC or 
systemd-nspawn.
