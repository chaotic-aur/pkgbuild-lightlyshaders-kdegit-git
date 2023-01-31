# Maintainer: Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix

pkgname=lightlyshaders-kdegit-git
pkgver=v2.0.0.r4.gd6d6ba9
pkgrel=1
pkgdesc="Round corners and outline effect for KWin"
arch=(x86_64)
url="https://github.com/a-parhom/LightlyShaders"
license=(GPL3)
depends=('qt5-x11extras' 'qt5-xmlpatterns' 'qt5-tools' 'kconfig-git' 'kconfigwidgets-git' 'ki18n-git' 'kcoreaddons-git' 'kcrash-git' 'kio-git' 'kservice-git' 'kinit-git' 'knotifications-git' 'kwin-git' 'kwidgetsaddons-git' 'kwindowsystem-git' 'kguiaddons-git' 'kglobalaccel-git' 'kde-dev-utils')
makedepends=('git' 'extra-cmake-modules-git')
provides=('lightlyshaders')
conflicts=('lightlyshaders')
source=("git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd LightlyShaders
  ( set -o pipefail
    git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

build() {
  cmake -DCMAKE_INSTALL_PREFIX=/usr -B build -S LightlyShaders
  make -C build
}

package() {
  make -C build DESTDIR="${pkgdir}" PREFIX=/usr install
}
