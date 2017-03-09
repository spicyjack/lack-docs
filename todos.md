## LACK TODOs ##

LACK partitioning layout
- `/boot` (ext2 filesystem)
- Everything else on `/` (Encrypted)
- `/home` (Encrypted, but with a different key than `/`, and mounted to
  `/home`)

Building `loop-aes`
- Download a copy of the Linux kernel (if needed)
  - `wget https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.9.3.tar.xz`
- Download the `loop-aes` tarball (if needed)
  - `wget http://loop-aes.sourceforge.net/loop-AES/loop-AES-v3.7j.tar.bz2`
- Download `util-linux` tarball (if needed)
  - `https://www.kernel.org/pub/linux/utils/util-linux/v2.28/util-linux-2.28.2.tar.xz`
- Unpack and build a kernel package with the `loop-aes` patches
- Unpack and build a patched copy of `util-linux`


vim: filetype=markdown shiftwidth=2 tabstop=2
