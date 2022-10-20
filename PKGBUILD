# Maintainer:  echo -n 'TWF0dCBDLiA8bWF0dEBnZXRjcnlzdC5hbD4='     | base64 -d
# Contributor: echo -n 'TWljaGFsIFMuIDxtaWNoYWxAZ2V0Y3J5c3QuYWw+' | base64 -d
# Contributor: echo -n 'Um9iaW4gQy4gPHJjYW5kYXVAZ2V0Y3J5c3QuYWw+' | base64 -d

pkgname=jade-gui
pkgver=1.6.1
pkgrel=1
pkgdesc='Libadwaita based GUI front-end for Jade'
license=('GPL3')
arch=('x86_64' 'aarch64')
url="https://github.com/crystal-linux/${pkgname}"
depends=('jade' 'openssl')
makedepends=('meson' 'ninja' 'libadwaita' 'desktop-file-utils' 'appstream-glib' 'gtk4')
source=("${pkgname}-${pkgver}::${url}/archive/v${pkgver}.tar.gz")
sha256sums=('bab9b7c33946faedf73865be73c95c4c9560aa3421892edf75ca6af6975dbaf9')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    meson --prefix="/usr" _build
    ninja -C _build
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}/_build"
    DESTDIR="${pkgdir}" ninja install
}
