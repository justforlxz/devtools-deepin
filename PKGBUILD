# Maintainer: justforlxz <justforlxz@gmail.com>

pkgname=devtools-deepin-git
pkgver=1.0.0
pkgrel=1
pkgdesc='Tools for Arch Linux package maintainers'
arch=('any')
license=('GPL')
url='https://github.com/justforlxz/devtools-deepin'
depends=('cmake' 'devtools')
makedepends=('git')
source=("$pkgname::git+https://github.com/justforlxz/devtools-deepin")
sha512sums=('SKIP')

pkgver() {
  cd ${pkgname}
  git describe --long --tags | sed -E 's,^[^0-9]*,,;s,([^-]*-g),r\1,;s,-,.,g'
}

build() {
  cd ${pkgname}
  cmake . -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd ${pkgname}
  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
