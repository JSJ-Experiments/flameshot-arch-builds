pkgname=flameshot-git
_pkgname=flameshot
pkgver=r1.0000000
pkgrel=1
pkgdesc="Powerful yet simple to use screenshot software"
arch=('x86_64')
url="https://github.com/JSJ-Experiments/flameshot"
license=('GPL-3.0-or-later')
depends=('qt6-base' 'qt6-svg' 'hicolor-icon-theme' 'kguiaddons')
makedepends=('git' 'cmake' 'ninja' 'qt6-tools')
optdepends=(
    'gnome-shell-extension-appindicator: tray icon support on GNOME'
    'xdg-desktop-portal: wayland screenshot support'
    'qt6-imageformats: additional export image formats'
)
provides=('flameshot')
conflicts=('flameshot')
source=("${_pkgname}::git+https://github.com/JSJ-Experiments/flameshot.git#branch=master")
sha256sums=('SKIP')

pkgver() {
    cd "${srcdir}/${_pkgname}"

    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cmake -GNinja -B build -S "${srcdir}/${_pkgname}" \
        -DCMAKE_BUILD_TYPE=None \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DUSE_WAYLAND_CLIPBOARD=1 \
        -DDISABLE_UPDATE_CHECKER=1

    cmake --build build
}

package() {
    DESTDIR="${pkgdir}" cmake --install build
}
