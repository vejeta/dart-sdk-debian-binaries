# dart-sdk riscv64 binaries, 3.13.4+dfsg1-5

The riscv64 bootstrap binary for [dart-sdk](https://tracker.debian.org/pkg/dart-sdk)
in Debian unstable. riscv64 has no dart-sdk in the archive yet, so its first
binary cannot be built by a buildd and has to be produced by hand with the
upstream stage0 seed. This repository exists only to hand that binary to the
sponsor; it is not a package archive and nothing here is meant to be installed
directly.

Built from the source already in unstable, `dart-sdk_3.13.4+dfsg1-5.dsc`, under
qemu-user emulation on an amd64 machine. Lintian reports 0 errors and 0
warnings. The packaging lives at
<https://salsa.debian.org/mendezr/dart-sdk>.

## Verifying

Verify the signature on the `.changes`, not the checksums below. The `.changes`
carries the SHA256 of every file and is signed with
`2A84 0ED0 0DE6 69F4 219B  8B33 02A7 9E3B 8215 1695`, the same key that signs
the uploads to mentors:

    gpg --verify dart-sdk_3.13.4+dfsg1-5_riscv64.changes

Once that is good, the checksums inside it are authenticated and `dscverify` or
`dput` will check the files against them. The list below is a convenience for
spotting a truncated download, nothing more: it lives in the same place as the
files, so it proves nothing on its own.

    07ba1d226ce435f61dfc2db8d3936d55b92d4d320f4a62db4e48045efef12207  dart-sdk-dbgsym_3.13.4+dfsg1-5_riscv64.deb
    c1c7e04ff435978f266d68f849a27039487ebf1f57fee9893633cbf8ed64b594  dart-sdk_3.13.4+dfsg1-5_riscv64.buildinfo
    6ed74167f6b7b7f0c59d4eff60e822dc9250c7eb9e618a9d749cd087493b8506  dart-sdk_3.13.4+dfsg1-5_riscv64.deb

## Uploading

Re-sign with your own key and upload; `debsign` replaces the signature:

    debsign -k <your key> dart-sdk_3.13.4+dfsg1-5_riscv64.changes
    dput ftp-master dart-sdk_3.13.4+dfsg1-5_riscv64.changes

## Building it yourself instead

`debian/README.source` in the packaging repository has the full recipe. It needs
no riscv64 hardware and no root, about 11 GB of disk, and between two and five
hours on an amd64 machine depending on how busy it is.
