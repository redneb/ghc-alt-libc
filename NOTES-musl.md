### musl based binary releases of GHC

#### Motivation

Static linking with glibc is problematic. On the other hand, static linking can simplify deployment and distribution of binaries. Unlike glibc, musl officially supports static linking and in fact it has been optimized for it.

#### Known issues

None so for.

#### Patches used

 * For 7.10.1: *none*.
 * For 7.8.4: [fix-execvpe-signature-ghc-7.8.4.patch](patches/fix-execvpe-signature-ghc-7.8.4.patch).
 * For 7.6.3: [fix-execvpe-signature-ghc-7.6.3.patch](patches/fix-execvpe-signature-ghc-7.6.3.patch).
