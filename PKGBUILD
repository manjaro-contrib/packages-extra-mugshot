# Maintainer: Somasis <somasis@cryptolab.net>
# Contributor: Bernhard Landauer <oberon@manjaro.org>

pkgname=mugshot
pkgver=0.4.1
pkgrel=1
pkgver_min=${pkgver%.*}
_git=01cc800f467dd3661bf158fb26820d37042fb0a0
pkgdesc="Program to update personal user details"
arch=('any')
url="https://launchpad.net/mugshot"
license=('GPLv3')
depends=('accountsservice'
	'gtk3'
	'python-cairo'
	'python-dbus'
	'python-distutils-extra'
	'python-gobject'
	'python-pexpect')
makedepends=('python-distutils-extra' 'intltool')
optdepends=('cheese: webcam support')
options=(!emptydirs)
source=("https://launchpad.net/mugshot/$pkgver_min/$pkgver/+download/mugshot-$pkgver.tar.gz"
	"avatars-$_git.tar.gz::http://github.com/oberon2007/avatars/archive/$_git.tar.gz")
md5sums=('80af444aa9e8f95732368af1923735e2'
         'feb11c6d8f7031df752b2c57c9e42ff8')

prepare() {
    cd $srcdir/$pkgname-$pkgver
    # patches here
}

package() {
    cd $srcdir/$pkgname-$pkgver
    python3 setup.py install --root $pkgdir

    # install our stock avatars
    cd $srcdir/avatars-$_git
    install -dm755 $pkgdir/usr/share/pixmaps
    cp -r faces $pkgdir/usr/share/pixmaps
}
