# Maintainer: Dominik Picheta <morfeusz8@gmail.com>
# Contributor: Sven-Hendrik Haase <sh@lutzhaase.com>
arch=('i686' 'x86_64')
pkgname=nimrod
pkgver=0.9.2
pkgrel=2
pkgdesc="A new statically typed, imperative programming language, that supports procedural, functional, object oriented and generic programming styles while remaining simple and efficient."
url="http://nimrod-code.org/"
license=("MIT")
depends=('glibc' 'readline')
conflicts=('nimrod-git')
source=("http://nimrod-code.org/download/nimrod_${pkgver}.zip")
md5sums=('2bdda551978126cd88d39a4cf0b6ab9c')

build() {
  cd ${srcdir}/nimrod

  chmod +x build.sh
  ./build.sh
  ./bin/nimrod c -d:release koch
  export PATH=$PATH:./bin/nimrod
  ./koch boot -d:release -d:useGnuReadline
}

package() {
  cd ${srcdir}/nimrod
  chmod +x install.sh
  ./install.sh $pkgdir/opt/
  mkdir -p $pkgdir/usr/
  mv $pkgdir/opt/nimrod/bin/ $pkgdir/usr/bin/
  mv $pkgdir/opt/nimrod/config/ $pkgdir/etc/
  mkdir -p $pkgdir/usr/share/nimrod/
  mkdir -p $pkgdir/usr/share/licenses/nimrod
  mv copying.txt $pkgdir/usr/share/licenses/nimrod/copying.txt
  mv $pkgdir/opt/nimrod/doc/ $pkgdir/usr/share/nimrod/doc/
  mkdir -p $pkgdir/usr/lib/
  mv $pkgdir/opt/nimrod/lib/ $pkgdir/usr/lib/nimrod/
  rm -r $pkgdir/opt
}
