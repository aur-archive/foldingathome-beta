# Maintainer: Evan Anderson <evan@thelinuxman.us>
# Contributor: paul2lv [at] gmail dot com

pkgname=foldingathome-beta
pkgver=7.4.2
pkgrel=1
pkgdesc="Folding@Home is a distributed computing project which studies protein folding, misfolding, aggregation, and related diseases."
arch=('i686' 'x86_64')
url="http://folding.stanford.edu/"
license=('CUSTOM')
depends=('glibc')
replaces=('foldingathome-v7' 'foldingathome')
conflicts=('foldingathome-v7' 'foldingathome')
install=foldingathome.install

# Moronic server
DLAGENTS=("https::/usr/bin/curl -k -o %o %u")

[ "$CARCH" = "i686" ] &&_source_arch="32bit"
[ "$CARCH" = "x86_64" ] && _source_arch="64bit"

if [ "$CARCH" = "i686" ]; then
    source=(https://fah.stanford.edu/file-releases/beta/release/fahclient/debian-testing-32bit/v7.4/fahclient_${pkgver}-32bit-release.tar.bz2 foldingathome.service)
    md5sums=('cde0774da10edc473ba865ac76064944' 'dd55dbae3fbe56f90bed0e40f2b0de3c')
     
elif [ "$CARCH" = "x86_64" ]; then
    source=(https://fah.stanford.edu/file-releases/beta/release/fahclient/debian-testing-64bit/v7.4/fahclient_${pkgver}-64bit-release.tar.bz2 foldingathome.service)
    md5sums=('d5af282ab3df65ada614d2580ffd3fcd' 'dd55dbae3fbe56f90bed0e40f2b0de3c')
fi


build() {
  cd ${srcdir}

  install -D -c -m755 fahclient_${pkgver}-${_source_arch}-release/FAHClient ${pkgdir}/opt/fah/FAHClient
  install -D -c -m755 fahclient_${pkgver}-${_source_arch}-release/FAHCoreWrapper ${pkgdir}/opt/fah/FAHCoreWrapper
  install -D -c -m755 fahclient_${pkgver}-${_source_arch}-release/sample-config.xml ${pkgdir}/opt/fah/sample-config.xml

  chmod 755 ${pkgdir}/opt/fah/FAHClient
  chmod 755 ${pkgdir}/opt/fah/FAHCoreWrapper
  install -D -m644 fahclient_${pkgver}-${_source_arch}-release/copyright ${pkgdir}/usr/share/licenses/${pkgname}/copyright
  install -D -m644 fahclient_${pkgver}-${_source_arch}-release/README ${pkgdir}/opt/fah/README
  install -D -m644 fahclient_${pkgver}-${_source_arch}-release/ChangeLog ${pkgdir}/opt/fah/ChangeLog
  install -D -m644 ${srcdir}/foldingathome.service ${pkgdir}/etc/systemd/system/foldingathome.service
}

