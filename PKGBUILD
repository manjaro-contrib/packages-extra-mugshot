# Maintainer: Bernhard Landauer <oberon@manjaro.org>
# Contributor: twa022 <twa022 at gmail dot com>
# Contributor: Somasis <somasis@cryptolab.net>

pkgname=mugshot
pkgver=0.4.3
pkgrel=6
pkgdesc="User profile configuration utility"
arch=('any')
url="https://bluesabre.org/projects/mugshot"
license=('GPL-3.0-or-later')
depends=(
  'accountsservice'
  'gtk3'
  'hicolor-icon-theme'
  'python-cairo'
  'python-gobject'
  'python-pexpect'
)
makedepends=(
  'python-build'
  'python-distutils-extra'
  'python-installer'
  'python-setuptools'
  'python-wheel'
)
checkdepends=('appstream')
optdepends=('cheese: webcam support')
_commit=01cc800f467dd3661bf158fb26820d37042fb0a0
source=("https://github.com/bluesabre/mugshot/releases/download/$pkgname-$pkgver/$pkgname-$pkgver.tar.gz"
        "avatars-$_commit.tar.gz::https://github.com/oberon-manjaro/avatars/archive/$_commit.tar.gz")
sha256sums=('2f66869a58bf45de29e065dfdaa591f32a88ec91682c0fa15accfd9f58c3c19c'
            'cf3a89089a63374b6b13e022f32c001e79e913dce6961fbe0f494cb5ed3cad90')

prepare() {
  cd "$pkgname-$pkgver"
  # patches here
}

build() {
  cd "$pkgname-$pkgver"
  python -m build --wheel --no-isolation
}

check() {
  cd "$pkgname-$pkgver"
  appstreamcli validate --no-net "data/metainfo/$pkgname.appdata.xml"
  desktop-file-validate build/share/applications/org.bluesabre.Mugshot.desktop
}

package() {
  cd "$pkgname-$pkgver"
  python -m installer --destdir="$pkgdir" dist/*.whl

  # install our stock avatars
  cd "$srcdir/avatars-$_commit"
  install -d "$pkgdir/usr/share/pixmaps"
  cp -r faces "$pkgdir/usr/share/pixmaps/"
}
