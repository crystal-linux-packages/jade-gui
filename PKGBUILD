# Maintainer:  echo -n 'TWF0dCBDLiA8bWF0dEBnZXRjcnlzdC5hbD4='     | base64 -d
# Contributor: echo -n 'TWljaGFsIFMuIDxtaWNoYWxAZ2V0Y3J5c3QuYWw+' | base64 -d
# Contributor: echo -n 'Um9iaW4gQy4gPHJjYW5kYXVAZ2V0Y3J5c3QuYWw+' | base64 -d

pkgname=jade-gui
pkgver=1.6.0
pkgrel=1
pkgdesc='Libadwaita based GUI front-end for Jade'
license=('GPL3')
arch=('x86_64' 'aarch64')
url="https://github.com/crystal-linux/${pkgname}"
depends=('jade' 'openssl')
makedepends=('meson' 'ninja' 'libadwaita' 'desktop-file-utils' 'appstream-glib' 'gtk4')
source=("${pkgname}-${pkgver}::${url}/archive/v${pkgver}.tar.gz")
sha256sums=('aa9ee575896f44bee706b6847de513549bd7aaaa663b13d84c8d7c07fe54accb')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    meson --prefix="${pkgdir}/usr" _build
    ninja -C _build
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}/_build"
    ninja install
    rm "${pkgdir}/usr/share/applications/mimeinfo.cache"
    rm "${pkgdir}/usr/share/glib-2.0/schemas/gschemas.compiled"
    rm "${pkgdir}/usr/share/icons/hicolor/icon-theme.cache"
    mv "${pkgdir}/usr/bin/jade_gui" "${pkgdir}/usr/bin/${pkgname}"
}
