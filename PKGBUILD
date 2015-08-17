# Maintainer: Gregor Robinson <gregor@fiatflux.co.uk>
# Contributor: Martin Perner <skinner33@fictionbox.de>

pkgname=pkcs11-helper-git
_gitname=pkcs11-helper
pkgver=5d412ba
pkgrel=1
pkgdesc="PKCS11 provider interaction library with a simple interface."
arch=('i686' 'x86_64')
url="http://www.opensc-project.org/opensc/wiki/pkcs11-helper"
license=('GPL' 'BSD')
depends=('gnutls' 'nss' 'openssl')
options=('!libtool')
conflicts=('pkcs11-helper')
provides=('pkcs11-helper')
source=('git+https://github.com/alonbl/pkcs11-helper.git')
md5sums=('SKIP')

pkgver() {
  cd $_gitname
  git describe --always | sed 's|-|.|g'
}

build() {
  cd $_gitname
  libtoolize
  aclocal
  autoheader
  automake --add-missing
  autoreconf -v
  ./configure --prefix=/usr
  make
}

package() {
  cd $_gitname
  make DESTDIR="${pkgdir}" install
  mkdir -p ${pkgdir}/usr/share/licenses/${_gitname}/
  install -Dm644 COPYING* "${pkgdir}/usr/share/licenses/${_gitname}/"
}
