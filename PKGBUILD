# Maintainer: Christopher Reimer <c[dot]reimer[at]googlemail[dot]com>
pkgname=vdr-vnsiserver
pkgver=20121125
_gitver=cae425bd
_vdrapi=1.7.35
pkgrel=3yavdr1
pkgdesc=""
url=""
arch=('x86_64' 'i686')
license=('GPL2')
depends=("vdr-api=${_vdrapi}")
install="$pkgname.install"
_plugname=$(echo $pkgname | sed 's/vdr-//g')
replaces=("vdr-plugin-$_plugname")
conflicts=("vdr-plugin-$_plugname")
source=("https://github.com/opdenkamp/xbmc-pvr-addons/archive/$_gitver.tar.gz")
md5sums=('4fb90c9db901f8b8ad5f8e48a992dbf7')

package() {
  cd ${srcdir}/xbmc-pvr-addons-${_gitver}*/addons/pvr.vdr.vnsi/vdr-plugin-${_plugname}

  mkdir -p $pkgdir/usr/lib/vdr/plugins
  make CFLAGS="$(pkg-config vdr --variable=cflags)" \
       CXXFLAGS="$(pkg-config vdr --variable=cxxflags)" \
       VDRDIR="/usr/include/vdr" \
       LIBDIR="$pkgdir/$(pkg-config vdr --variable=libdir)" \
       LOCALEDIR="$pkgdir/$(pkg-config vdr --variable=locdir)"

  mkdir -p $pkgdir/var/lib/vdr/plugins
  cp -r vnsiserver $pkgdir/var/lib/vdr/plugins
}
