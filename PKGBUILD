# Maintainer: Yukicanis <yukicanis.@gmail.com>
# Contributor: Scimmia <Scimmia22@outlook.com>

pkgname=xf86-video-wlglamor-git
pkgver=1.0.0.r2.3328b2f
pkgrel=1
pkgdesc="XWayland DDX based on Glamor"
arch=('i686' 'x86_64')
url="https://github.com/axeldavy/xf86-video-wlglamor"
makedepends=('xwayland-git' 'glamor-egl' 'git' 'xorg-util-macros' 'randrproto'
             'inputproto' 'videoproto' 'xf86driproto' 'glproto' 'dri2proto'
             'xineramaproto' 'xf86dgaproto' 'resourceproto' 'scrnsaverproto')
license=('custom')
source=('git+https://github.com/axeldavy/xf86-video-wlglamor.git')
md5sums=('SKIP')

build() {
  cd $srcdir/xf86-video-wlglamor
  ./autogen.sh --prefix=/usr
  make
}

package() {
  cd $srcdir/xf86-video-wlglamor
  make DESTDIR="${pkgdir}" install 
  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/"
}

pkgver() {
  cd $srcdir/xf86-video-wlglamor
  echo $(awk -F [][] '/AC_INIT/ {getline;print $2}' configure.ac).\
r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}
