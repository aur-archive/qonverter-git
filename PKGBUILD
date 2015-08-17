# Maintainer: Martin Rotter <rotter.martinos@gmail.com>

pkgname=qonverter-git
pkgver=20130515
pkgrel=1
pkgdesc='Very simple and easy-to-use desktop calculator with unusual functions.'
arch=('i686' 'x86_64')
url="http://code.google.com/p/qonverter"
license=('GPL3')
depends=(qt5-base)
makedepends=(gcc git cmake)
conflicts=(qonverter)

_gitname=qonverter
_gitroot=https://Rotter.Martinos@code.google.com/p/qonverter/

build() {
  cd ${srcdir}
  msg "Cloning " ${_gitname} " repository..."
  
  if [ -d ${_gitname} ] ; then
    cd ${_gitname} && git pull origin master
    msg "The local files are updated."
  else
    git clone ${_gitroot}
  fi

  msg "Git checkout done or server timeout."
  cd ${srcdir}/${_gitname}

  if [ ! -d "build" ]; then
    mkdir build
  fi
  
  cd build

  msg "Preparing files with cmake..."
  cmake ../ -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=release
}

package() {
  cd ${srcdir}/${_gitname}/build

  msg "Compiling files..."
  make DESTDIR=${pkgdir} install || return 1

  msg "All files were successfully compiled."
}
