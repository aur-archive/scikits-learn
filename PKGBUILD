# Maintainer: Andrzej Giniewicz <gginiu@gmail.com>

pkgname=scikits-learn
pkgver=0.13.1
pkgrel=1
pkgdesc="A set of python modules for machine learning and data mining"
arch=('i686' 'x86_64')
url="http://scikit-learn.sourceforge.net/"
license=('BSD')
depends=('python2-scipy')
makedepends=('python2-distribute')
options=(!emptydirs)

source=("http://downloads.sourceforge.net/project/scikit-learn/scikit-learn-${pkgver}.tar.gz" 
        "LICENSE")
md5sums=('acba398e1d46274b8470f40d0926e6a4'
         '327083d2576cc0aad1b8f10b2bcd2974')

build() {
  cd "$srcdir"/scikit-learn-$pkgver

  unset LDFLAGS

  python2 setup.py build
}

package() {
  cd "$srcdir"/scikit-learn-$pkgver

  python2 setup.py install --root="$pkgdir"/ --optimize=1

  sed -i -e "s|#![ ]*/usr/bin/python$|#!/usr/bin/python2|" \
         -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" \
    $(find "${pkgdir}" -name '*.py')

  install -D "$srcdir"/LICENSE "$pkgdir"/usr/share/licenses/scikits-learn/LICENSE
}

