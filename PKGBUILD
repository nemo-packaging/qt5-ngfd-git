## $Id$
# Maintainer: TheKit <nekit1000 at gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=libngf-qt-git
pkgver=0.6.4.r0.g1f3ec8d
pkgrel=1
pkgdesc="Qt-based client library for Non-Graphic Feedback daemon"
arch=('x86_64' 'aarch64')
url="https://git.sailfishos.org/mer-core/libngf-qt"
license=('GPL')
depends=('qt5-base' 'qt5-declarative' 'libngf')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=('git+https://git.sailfishos.org/mer-core/libngf-qt.git')
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
	cd "$srcdir/${pkgname%-git}"
	qmake PREFIX=/usr
	
	# Hack for PREFIX path not being passed to src subproject for some reason
	cd src
	qmake PREFIX=/usr
	cd ..

	make
}

package() {
	cd "$srcdir/${pkgname%-git}"
	make INSTALL_ROOT="$pkgdir/" install
}
