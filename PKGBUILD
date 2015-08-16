# Maintainer: Arthur Darcet <arthur.darcet@m4x.org>

pkgname=libccv
pkgver=0.4
pkgrel=4
_srcdir=liuliu-ccv-e8eb24b
pkgdesc='A Modern Computer Vision Library, with a libccv.so shared library'
arch=('x86_64' 'i386')
url='http://libccv.org'
license=('custom')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/liuliu/ccv/tarball/stable" 'config.mk' 'makefile-libccv.so.patch')
md5sums=('cc6de6251dec751568c1b0292056e621' '1577f766c9131047d12a0f23409d03df' 'ad57801b024dee36307b58c5617e9c93')
depends=('libpng' 'gsl' 'fftw' 'cblas' 'python-liblinear')

build() {
  cd "${srcdir}/${_srcdir}/lib"
  patch -Np1 -i "${startdir}/makefile-libccv.so.patch"
  cp "${startdir}/config.mk" ./
  make all
}

package() {
  cd "$srcdir/${_srcdir}/lib"
  install -D -m644 ccv.h "${pkgdir}/usr/include/ccv.h"
  install -D -m644 ccv_internal.h "${pkgdir}/usr/include/ccv_internal.h"
  install -D -m644 libccv.a "${pkgdir}/usr/lib/libccv.a"
  install -D -m755 libccv.so "${pkgdir}/usr/lib/libccv.so.${pkgver}"
  cd "${pkgdir}/usr/lib"
  ln -s libccv.so.${pkgver} libccv.so.0
  ln -s libccv.so.${pkgver} libccv.so
}
