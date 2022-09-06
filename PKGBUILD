# Maintainer:  echo -n 'TWljaGFsIFMuIDxtaWNoYWxAZ2V0Y3J5c3QuYWw+' | base64 -d
# Contributor: echo -n 'YXh0bG9zIDxheHRsb3NAZ2V0Y3J5c3QuYWw+'     | base64 -d

pkgname=jade-gui
pkgver=1.1.4
pkgrel=3
pkgdesc='Libadwaita based GUI front-end for Jade'
license=('GPL3')
arch=('any')
url="https://github.com/crystal-linux/$pkgname"
depends=('jade' 'openssl' 'flatpak')
makedepends=('flatpak-builder' 'git')
source=("jade-gui-git::git+${url}#tag=v$pkgver")
sha256sums=('SKIP')

build() {
    cd "$srcdir/$pkgname-git"
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
    flatpak-builder --install-deps-from=flathub --repo=../build-repo --force-clean ../build-dir al.getcryst.jadegui.yml
    flatpak build-bundle ../build-repo --runtime-repo=https://flathub.org/repo/flathub.flatpakrepo ../jade-gui.flatpak al.getcryst.jadegui
}

package() {
    install -Dm 0755 jade-gui.flatpak "$pkgdir/usr/share/jade-gui/."
    install -Dm 0755 ../jade-gui "$pkgdir/usr/bin/."
}
