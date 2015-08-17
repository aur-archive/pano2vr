# Contributor: Ismael Barros (RazZziel) <razielmine@gmail.com>
# Maintainer: Luigi Ranghetti <ggranga@gmail.com>

pkgname=pano2vr
pkgver=4.5.1
_pkgver2=`echo $pkgver | tr '.' '_'`
pkgrel=2
pkgdesc="Converts panoramic images into QuickTime VR or Macromedia Flash formats."
url="http://gardengnomesoftware.com/pano2vr.php"
license=('Pano2VR')
arch=(x86_64)
depends=('libgl' 'qt4' 'qtwebkit')
source=(http://gardengnomesoftware.com/download/${pkgname}/${pkgname}_linux64_${_pkgver2}.tar.gz
        'changedir.patch'
        'pano2vr.desktop')
md5sums=('4ae4c1cbd9eac30e33efec79e0b8d5bb'
         '0fd71d2d76982a5146dd23fce94ec942'
         '55617407038824cbc0fbeb01bff2ea0c')

prepare() {
  cd "$srcdir"
  patch -p1 -i "$srcdir/changedir.patch"
}

build() {
  install -d $pkgdir/opt/
  cp -r $srcdir $pkgdir/opt/
  mv $pkgdir/opt/src $pkgdir/opt/$pkgname

  install -d $pkgdir/usr/local/bin/
  ln -s /opt/$pkgname/$pkgname.sh $pkgdir/usr/local/bin/$pkgname

  install -d $pkgdir/usr/share/licenses/common/Pano2VR/
  install -m644 $srcdir/license.txt $pkgdir/usr/share/licenses/common/Pano2VR/

  install -D -m644 $srcdir/${pkgname}_icon.png $pkgdir/usr/share/pixmaps/${pkgname}.png
  install -D -m644 $srcdir/${pkgname}.desktop $pkgdir/usr/share/applications/${pkgname}.desktop 
}
