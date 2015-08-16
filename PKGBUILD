# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kfilemetadata-frameworks-git
pkgver=r133.e4b6a38
pkgrel=1
pkgdesc="A library for extracting file metadata"
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/kdelibs/kfilemetadata'
license=('LGPL')
depends=('kservice-git' 'karchive-git' 'exiv2' 'poppler-qt5' 'taglib' 'ffmpeg' 'ebook-tools')
makedepends=('extra-cmake-modules' 'git')
provides=('kfilemetadata-frameworks')
conflicts=('kfilemetadata-frameworks')
source=('git://anongit.kde.org/kfilemetadata#branch=frameworks')
md5sums=('SKIP')

pkgver() {
  cd kfilemetadata
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kfilemetadata \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_PREFIX_PATH=/usr/lib/cmake \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DQT_PLUGIN_INSTALL_DIR=lib/qt/plugins \
    -DLIB_INSTALL_DIR=lib
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
