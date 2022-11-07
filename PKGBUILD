# Maintainer: Ole Martin Ruud

_pkgname=watson
pkgname=$_pkgname-barskern_git
pkgver=2.1.0.r3.g14604a3e21
pkgrel=1
pkgdesc='A wonderful CLI to track your time! With patches from barskern'
arch=('any')
#url='https://tailordev.github.io/Watson/'
url='https://github.com/barskern/Watson.git'
license=('MIT')
depends=(
    'python'
    'python-arrow'
    'python-click'
    'python-click-repl'
    'python-click-didyoumean'
    'python-requests'
)
makedepends=('git' 'python-setuptools')
options=(!emptydirs)

provides=("$_pkgname")
conflicts=("$_pkgname")

source=("$_pkgname::git+$url")
sha256sums=('SKIP')

pkgver() {
	cd "$_pkgname"
	echo $(git describe --abbrev=10 --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g')
}

build() {
	cd "$_pkgname"
    python setup.py build
}

package() {
	cd "$_pkgname"

    install -D -m 644 LICENSE "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
    install -D -m 644 watson.completion "$pkgdir/usr/share/bash-completion/completions/$_pkgname"
    install -D -m 644 watson.zsh-completion "$pkgdir/usr/share/zsh/site-functions/_$_pkgname"
    install -D -m 644 watson.fish "$pkgdir/usr/share/fish/completions/$_pkgname.fish"

    python setup.py install --root="$pkgdir" --optimize=1
}
