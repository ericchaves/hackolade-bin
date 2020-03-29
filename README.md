Hackolade Arch installer
========================

# To install
- clone repository and enter it
- run `makepkg -si`

# To upgrade

- update the number version in PKGBUILD
- run `makepkg -si` - it will download the new zip and fail the sha256 checksum
- run `sha256sum hackolade_x64_${VERSION}.zip` replacing the ${VERSION} by the new version number to get the correct sha256 checksum
- update the ckecksum value with the one you got from sha256sum output (line 20).
- run `makepkg -si` again
