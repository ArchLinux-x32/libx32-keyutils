# $Id: PKGBUILD 108849 2014-04-05 08:08:31Z bluewind $
# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
_pkgbasename=keyutils
pkgname=lib32-$_pkgbasename
pkgver=1.5.9
pkgrel=1
pkgdesc="Linux Key Management Utilities (32-bit)"
arch=(x86_64)
url="http://www.kernel.org"
license=('GPL2' 'LGPL2.1')
depends=(lib32-glibc $_pkgbasename)
makedepends=(gcc-multilib)
source=(http://people.redhat.com/~dhowells/$_pkgbasename/$_pkgbasename-$pkgver.tar.bz2)
md5sums=('7f8ac985c45086b5fbcd12cecd23cf07')

build() {
  cd "$srcdir/$_pkgbasename-$pkgver"
  
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  sed -i -e 's/^\(USR\)\?LIBDIR\s*:=.*$/\1LIBDIR=\/usr\/lib32/' Makefile
  make CFLAGS="${CFLAGS}" LDFLAGS="${LDFLAGS}"
}

package() {
  cd "$srcdir/$_pkgbasename-$pkgver"
  make DESTDIR="$pkgdir" install

  rm -rf "${pkgdir}"/{usr/{include,share,bin,sbin},etc,{s,}bin}
}
