# Maintainer: Tarjaizaid <tarjaizaid@gmail.com>
# based on gns3 pkgbuild https://aur.archlinux.org/packages.php?ID=23825
# Contributor: max-k <max-k@post.com>
pkgname=gns3-vbe
pkgver=0.8.1
pkgrel=1
pkgdesc="Unofficial version with VirtualBox support of Graphical network simulator that allows simulation of complex networks."
arch=(i686 x86_64)
url="http://www.gns3.net/"
license=('GPL')
depends=('python2-pyqt' 'python2-sip' 'dynamips' 'inetutils')
optdepends=('qemu' 'wireshark' 'virtualbox' 'virtualbox-sdk' 'xdotool')
conflicts=(gns3)
source=("http://downloads.sourceforge.net/gns-3/GNS3-${pkgver}-src-vbox-2011-07-29.tar.bz2")
md5sums=('45a845d23a2213316943428054030207')

build() {
  cd ${srcdir}/GNS3-${pkgver}
  python2 setup.py build
  python2 setup.py install --prefix  ${pkgdir}/usr
  gzip ./docs/man/gns3.1
  install -D -m 644 ./docs/man/gns3.1.gz ${pkgdir}/usr/share/man/man1/gns3.1.gz
  #sed -i 's/#!\/usr\/bin\/env python/#!\/usr\/bin\/env python2/' ./qemuwrapper/qemuwrapper.py
  install -D -m 755 ${srcdir}/GNS3-${pkgver}/qemuwrapper/qemuwrapper.py ${pkgdir}/usr/share/GNS3/qemuwrapper.py
  install -D -m 755 ${srcdir}/GNS3-${pkgver}/vboxwrapper/vboxwrapper.py ${pkgdir}/usr/share/GNS3/vboxwrapper.py
  install -D -m 755 ${srcdir}/GNS3-${pkgver}/vboxwrapper/vboxcontroller_4_1.py ${pkgdir}/usr/share/GNS3/vboxcontroller_4_1.py
  install -D -m 755 ${srcdir}/GNS3-${pkgver}/vboxwrapper/vboxtestcase.py ${pkgdir}/usr/share/GNS3/vboxtestcase.py
}
