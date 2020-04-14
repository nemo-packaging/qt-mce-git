## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt5-mce-git
_pkgname=qt-mce-git
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
provides=("${pkgname}-git" "${_pkgname}-git")
conflicts=("${pkgname}-git" "${_pkgname}-git")
source=(
  "${_pkgname}::git+${url}")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/${_pkgname}"
  ( set -o pipefail
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  ) 2>/dev/null
}

build() {
  cd "${srcdir}/${_pkgname}"
  mkdir -p build
  cd build
  qmake ..
  make
}

package() {
  cd "${srcdir}/${_pkgname}"
  cd build
  make INSTALL_ROOT="${pkgdir}" install
}
