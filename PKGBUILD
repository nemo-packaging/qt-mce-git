## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt-mce-git
_srcname=qt-mce
pkgver=1.4.2.r0.g431168d
pkgrel=1
_project=mer-core
_branch=master
pkgdesc="A library of Qt bindings for mce"
arch=('x86_64' 'aarch64')
url="https://git.sailfishos.org/$_project/libmce-qt#branch=$_branch"
license=('BSD-3-Clause')
depends=('qt5-base' 'qt5-declarative')
makedepends=('git' 'mce-git')
optdepends=()
provides=("${_srcname}")
conflicts=()
source=(
  "${pkgname}::git+${url}")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  ( set -o pipefail
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  ) 2>/dev/null
}

build() {
  cd "${srcdir}/${pkgname}"
  mkdir -p build
  cd build
  qmake ..
  make
}

package() {
  cd "${srcdir}/${pkgname}"
  cd build
  make INSTALL_ROOT="${pkgdir}" install
}
