# Contributor: actnlzz <actnlzz AT gmail MF com>
# Contributor: Taijian <taijian@posteo.de>
# Contributor: Mohammadreza Abdollahzadeh <morealaz at gmail dot com>

pkgbase=oomox-qt-styleplugin-git
pkgname=(oomox-qt5-styleplugin-git oomox-qt6-styleplugin-git)
pkgver=1.4.1.r25.g58805cb
pkgrel=1
pkgdesc='A style to bend Qt applications to look like they belong into themix/oomox, git package.'
arch=(x86_64)
url='https://github.com/themix-project/oomox-qt-styleplugin'
license=(GPL)
makedepends=(cmake git qt5-x11extras qt6-base)
source=("${pkgbase%-git}::git+${url}.git")
sha512sums=('SKIP')

pkgver() {
	cd "${pkgbase%-git}"
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cmake -B build-qt5 -S ${pkgbase%-git} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DUSE_QT6=OFF
  cmake --build build-qt5

  cmake -B build-qt6 -S ${pkgbase%-git} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DUSE_QT6=ON
  cmake --build build-qt6
}

package_oomox-qt5-styleplugin-git() {
  pkgdesc='A style to bend Qt5 applications to look like they belong into themix/oomox, git version'
  depends=(qt5-base)
  optdepends=('qt5-x11extras: For X11 and/or xwayland support')
  conflicts=(oomox-qt oomox-qt5)
  provides=(oomox-qt5 oomox-qt-git)

  DESTDIR="$pkgdir" cmake --install build-qt5
}

package_oomox-qt6-styleplugin-git() {
  pkgdesc='A style to bend Qt6 applications to look like they belong into themix/oomox, git version'
  depends=(qt6-base)
  conflicts=(oomox-qt6)
  provides=(oomox-qt6)

  DESTDIR="$pkgdir" cmake --install build-qt6
}
