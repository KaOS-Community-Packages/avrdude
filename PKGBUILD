pkgname=avrdude
pkgrel=1
pkgver=20151216.1366
pkgdesc="AVRDUDE is an utility to download/upload/manipulate the ROM and EEPROM contents of AVR microcontrollers using the in-system programming technique (ISP)."
arch=('x86_64')
url="http://www.nongnu.org/avrdude/"
license=('GPL')
depends=('libftdi' 'libusb-compat' 'elfutils')
source=("${pkgname}::svn+http://svn.savannah.nongnu.org/svn/avrdude/trunk")
md5sums=('SKIP')

build() {
  cd "${srcdir}/${pkgname}/${_pkgname}"
  ./bootstrap
  ./configure --mandir=/usr/share/man \
    --prefix=/usr \
    --sysconfdir=/etc \
    --enable-linuxgpio
  make
}

package() {
  cd "${srcdir}/${pkgname}/${_pkgname}"

  make DESTDIR="${pkgdir}/" install
}

pkgver() {
  cd "${srcdir}/${pkgname}"
  svn info | awk '/Revision/{r=$2}/Date/{gsub(/-/,"");d=$4}END{print d"."r}'
}
