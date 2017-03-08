## LACK TODOs ##

LACK partitioning layout
- `/boot` (ext2 filesystem)
- Everything else on `/` (Encrypted)
- `/home` (Encrypted, but with a different key than `/`, and mounted to
  `/home`)

Building `loop-aes`
- Download the `loop-aes` tarball (if needed)
- Download `util-linux` tarball (if needed)
- Download a copy of the Linux kernel (if needed)
- Unpack and build a patched copy of `util-linux`
- Unpack and build a kernel package with the `loop-aes` patches

vim: filetype=markdown shiftwidth=2 tabstop=2
