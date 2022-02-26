# Maintainer: Bernhard Landauer <oberon@manjaro.org>

# Arch credits:
# Maintainer: twa022 <twa022 at gmail dot com>
# Contributor: Somasis <somasis@cryptolab.net>

pkgname=mugshot
pkgver=0.4.3
pkgrel=3
_git=01cc800f467dd3661bf158fb26820d37042fb0a0
pkgdesc="Program to update personal user details"
arch=('any')
url="https://bluesabre.org/projects/mugshot"
license=('GPL3')
depends=('accountsservice'
  'gtk3'
  'hicolor-icon-theme'
  'python'
  'python-cairo'
  'python-gobject'
  'python-pexpect')
makedepends=('python-distutils-extra')
optdepends=('cheese: webcam support')
options=(!emptydirs)
source=("https://github.com/bluesabre/mugshot/releases/download/$pkgname-$pkgver/$pkgname-$pkgver.tar.gz"
        "avatars-$_git.tar.gz::https://github.com/oberon-manjaro/avatars/archive/$_git.tar.gz")
sha256sums=('2f66869a58bf45de29e065dfdaa591f32a88ec91682c0fa15accfd9f58c3c19c'
            'cf3a89089a63374b6b13e022f32c001e79e913dce6961fbe0f494cb5ed3cad90')

prepare() {
    cd "$pkgname-$pkgver"
    # patches here
}

package() {
    cd "$pkgname-$pkgver"
    python setup.py install --root="$pkgdir" --optimize=1

    # install our stock avatars
    cd "$srcdir/avatars-$_git"
    install -d "$pkgdir/usr/share/pixmaps"
    cp -r faces "$pkgdir/usr/share/pixmaps/"
}
