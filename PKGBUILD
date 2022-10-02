# Maintainer:  echo -n 'TWljaGFsIFMuIDxtaWNoYWxAZ2V0Y3J5c3QuYWw+' | base64 -d
# Contributor: echo -n 'YXh0bG9zIDxheHRsb3NAZ2V0Y3J5c3QuYWw+'     | base64 -d

pkgname=jade-gui
_pkgname=jadegui
pkgver=1.5.0
pkgrel=2
pkgdesc='Libadwaita based GUI front-end for Jade'
license=('GPL3')
arch=('any')
url="https://github.com/crystal-linux/${pkgname}"
depends=('jade' 'openssl' 'flatpak')
makedepends=('flatpak-builder')
source=("${pkgname}-${pkgver}::${url}/archive/v${pkgver}.tar.gz")
sha256sums=('b1c8454d03ae322607f5af88b3bfb2dcde9bfd15642ba6e8adb0b8dbdab0d94e')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
    flatpak-builder --install-deps-from=flathub --repo=../build-repo --force-clean ../build-dir al.getcryst.${_pkgname}.yml
    flatpak build-bundle ../build-repo --runtime-repo=https://flathub.org/repo/flathub.flatpakrepo ../${pkgname}.flatpak al.getcryst.${_pkgname}
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    install -Dm 755 "${pkgname}.flatpak" "${pkgdir}/usr/share/${pkgname}/${pkgname}.flatpak"
    install -Dm 755 "../${pkgname}" "$pkgdir/usr/bin/${pkgname}"
    install -Dm 644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
