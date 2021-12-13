# Maintainer: Somasis <somasis@cryptolab.net>
# Contributor: Bernhard Landauer <oberon@manjaro.org>

pkgname=mugshot
pkgver=0.4.3
pkgrel=2
pkgver_min=${pkgver%.*}
_git=01cc800f467dd3661bf158fb26820d37042fb0a0
pkgdesc="Program to update personal user details"
arch=('any')
url="https://launchpad.net/mugshot"
license=('GPLv3')
depends=('accountsservice'
  'dbus-python'
  'gtk3'
  'hicolor-icon-theme'
  'python'
  'python-cairo'
  'python-gobject'
  'python-pexpect')
makedepends=('python-distutils-extra' 'intltool')
optdepends=('cheese: webcam support')
options=(!emptydirs)
source=("https://github.com/bluesabre/mugshot/releases/download/mugshot-$pkgver/mugshot-$pkgver.tar.gz"
        "avatars-$_git.tar.gz::http://github.com/oberon2007/avatars/archive/$_git.tar.gz")
md5sums=('1c504dcec181159ff5aa896bed9605ab'
         'feb11c6d8f7031df752b2c57c9e42ff8')

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
    cp -r faces "$pkgdir/usr/share/pixmaps"
}
