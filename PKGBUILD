# Maintainer: JadenJSJ <jadenjsj@proton.me>
# Contributor: Dana Jansens, Max Lv

_modname=tcp_china
pkgname=${_modname}-dkms
pkgver=1.0
pkgrel=1
pkgdesc="TCP-CHINA Congestion control algorithm, based on very few modifications to TCP-AFRICA (Unfair TCP, do not use!) "
arch=('any')
url="https://github.com/madeye/tcp_china/"
license=('GPL')
depends=('dkms')
optdepends=('linux-headers' 'linux-lts-headers' 'linux-hardened-headers' 'linux-rt-headers' 'linux-rt-lts-headers' 'linux-zen-headers')
source=("${_modname}.c"
        "Makefile"
        "dkms.conf")
sha256sums=('b3513c86b87c1c8d21a1809a4d9f3d2e384147e04d364bff126cb52134fdf168'
            'a16fc7fbf20972deb76c137d871a8288df8b6d6985a59f663ae4f2a09dcbfc46'
            '4e5a7702ebf1a465e25b8865de3668c450d0a1022a5dedb734a3ca04d7fa2629')

prepare() {
  # Replace placeholder in dkms.conf with actual version
  sed -i "s/@PKGVER@/${pkgver}/" dkms.conf
}

# build() empty, DKMS handles the build.

package() {
  # Install source files for DKMS
  install -Dm644 "${_modname}.c" "$pkgdir/usr/src/${_modname}-${pkgver}/${_modname}.c"
  install -Dm644 Makefile "$pkgdir/usr/src/${_modname}-${pkgver}/Makefile"

  # Install DKMS config file
  install -Dm644 dkms.conf "$pkgdir/usr/src/${_modname}-${pkgver}/dkms.conf"

  # Install license
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/${pkgname}/LICENSE"
}
