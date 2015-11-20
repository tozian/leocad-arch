# Contributor: Seth Schroeder <theking@kingdomofseth.com>
# Contributor: Sven Schneider <archlinux.sandmann@googlemail.com>
 
pkgname=leocad
pkgver=0.82.2
_piecesver=9088
pkgrel=1
pkgdesc="LeoCAD is a CAD program for creating virtual LEGO models. It 
has an easy to use interface and currently includes over 6000 different 
pieces created by the LDraw community."
arch=('i686' 'x86_64')
url="http://leocad.org"
license=('GPL')
makedepends=('qtchooser')
depends=('zlib' 'libjpeg' 'libpng' 'gtk2' 'mesa')
source=(https://github.com/tozian/leocad-arch/raw/master/source/LeoCAD-Source-${pkgver}.tgz
http://github.com/tozian/leocad-arch/raw/master/source/Library-Linux-${_piecesver}.zip
leocad.sh)
md5sums=('dbc6ff61fb687e67cc38d26d453d5fdb'
'e9e2456992ab5f98fa276206172ca31d'
'cbe0189f828a7cf6a42754352a72eeac')
 
build() {
cd "${srcdir}/${pkgname}"
 
# install the binary to /usr/share
qmake-qt4 leocad.pro
sed 's#$(INSTALL_ROOT)/usr/bin#$(INSTALL_ROOT)/usr/share/leocad/bin#g' -i Makefile
make
}
 
package() {
cd "${srcdir}/${pkgname}"
 
make INSTALL_ROOT="${pkgdir}" install
 
install -dm755 "${pkgdir}/usr/share/leocad/pieces/"
install -Dm644 "${srcdir}/library.bin" "${pkgdir}/usr/share/leocad/pieces/library.bin"
 
install -dm755 "${pkgdir}/usr/bin/"
install -Dm755 "${srcdir}/leocad.sh" "${pkgdir}/usr/bin/leocad"
}

