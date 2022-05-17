# Maintainer: justforlxz <justforlxz@gmail.com>

pkgname=devtools-deepin-git
_pkgname=devtools
pkgver=1.0.0
pkgrel=1
pkgdesc='Tools for Arch Linux package maintainers'
arch=('any')
license=('GPL')
url='https://github.com/deepin-community/devtools-deepin'
depends=('bash' 'openssh' 'subversion' 'rsync' 'arch-install-scripts'
         'git' 'bzr' 'mercurial' 'diffutils' 'util-linux' 'awk')
makedepends=('asciidoc' 'git')
optdepends=('btrfs-progs: btrfs support')
provides=($_pkgname=${pkgver%%.r*})
conflicts=($_pkgname)
source=("$pkgname::git+https://github.com/deepin-community/devtools-deepin")
sha512sums=('SKIP')

pkgver() {
  cd ${pkgname}
  git describe --long --tags | sed -E 's,^[^0-9]*,,;s,([^-]*-g),r\1,;s,-,.,g'
}

build() {
  cd ${pkgname}
  make BUILDTOOLVER="${pkgver}-${pkgrel}-${arch}" PREFIX=/usr
}

package() {
  cd ${pkgname}
  make PREFIX=/usr DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
