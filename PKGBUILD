# Maintainer: Eric Chaves <eric at craftti dot com dot br>

pkgname=hackolade-bin
_pkgname=hackolade
pkgver=3.6.8
pkgrel=1
pkgdesc="Hackolade: Visual data modeling tool for NoSQL databases. (UNOFFICIAL)"
arch=('x86_64')
url="https://hackolade.com/"
license=('custom: commercial')
makedepends=('unzip')
provides=('hackolade')
conflicts=('hackolade')
options=(!strip)
noextract=("hackolade_x64_${pkgver}.zip")
 
source=("hackolade_x64_${pkgver}.zip::https://s3-eu-west-1.amazonaws.com/hackolade/current/Hackolade-linux-x64.zip"
        "hackolade.desktop::https://raw.githubusercontent.com/ericchaves/hackolade-bin/master/hackolade.desktop]")

sha256sums=('9f44ec196636147f70055ce88b6add28c77510dfe6630e5040b0a193393a13b5'
            '1d2c2e8b662f4f36bc8fc87c918d422cb1f6096c9929c2691312b5aee3f90f07')

build(){
  unzip -q  "${srcdir}/hackolade_x64_${pkgver}.zip" -d "${srcdir}/hackolade_x64_${pkgver}"
}

package() {
  # some times the source package is compressed with different folder structure
  # check the source zip file and adjust accordingly in case of errors
  _srcdir="${srcdir}/hackolade_x64_${pkgver}/home/eduard/Develop/Hackolade/release/linux-x64/Hackolade-linux-x64"
 
  install -d "${pkgdir}/usr/share/licenses/${_pkgname}"
  install -d "${pkgdir}/usr/bin"
  install -d "${pkgdir}/usr/share/applications"
  install -d "${pkgdir}/usr/share/icons"
  install -d "${pkgdir}/opt/${_pkgname}"

  # .desktop file does not belog to sourc package so we need to copy it from srcdir
  install -m644 "${srcdir}/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"

  install -m644 "${_srcdir}/License.txt" "${pkgdir}/usr/share/licenses/${_pkgname}/License.txt"
  install -m644 "${_srcdir}/resources/app/icon.png" "${pkgdir}/usr/share/icons/${_pkgname}.png"

  cp -r "${_srcdir}/"* "${pkgdir}/opt/${_pkgname}" -R

  ln -s "/opt/${_pkgname}/Hackolade" "${pkgdir}/usr/bin/hackolade"
}