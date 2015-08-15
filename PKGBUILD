#Contributor: Sebastien Piccand <sebcactus gmail com>
pkgname=eo
pkgver=1.3.1
pkgrel=2
pkgdesc="EO is a templates-based, ANSI-C++ compliant evolutionary computation library"
arch=('i686' 'x86_64')
url="http://eodev.sourceforge.net/"
license=('LGPL')
conflicts=('galib')
makedepends=('cmake')
source=(http://downloads.sourceforge.net/project/eodev/$pkgname/$pkgver/EO-$pkgver.zip)
md5sums=('99ebeff7bc7cab2db7b7ec0bff2289ca')

build() {
  cd "$srcdir"
	# Patch for compatibility with gcc-4.7
	sed -i 's|func(eo)|this->func(eo)|' $pkgname/src/eoEvalFuncCounterBounder.h
  mkdir $pkgname-build
  cd $pkgname-build
  cmake -DCMAKE_INSTALL_PREFIX="/usr" -DCMAKE_CXX_FLAGS="$CXXFLAGS" ../$pkgname
  make
}

package() {
  cd "$srcdir"/$pkgname-build
  make DESTDIR="$pkgdir" install
  # clean build
  rm -r "$srcdir"/$pkgname-build
}
