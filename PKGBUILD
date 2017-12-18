pkgname=neomutt
pkgver=20171215
pkgrel=1
pkgdesc='Small but powerful text-based mail client'
url='http://www.neomutt.org/'
license=('GPL')
arch=('x86_64')
depends=('mime-types' 'notmuch-runtime' 'lua' 'lmdb')
optdepends=(
    'urlview: for url menu'
    'python: keybase.py'
)
makedepends=('git' 'gnupg' 'libxslt' 'docbook-xsl')
source=("https://github.com/neomutt/neomutt/archive/$pkgname-$pkgver.tar.gz"
        "https://github.com/neomutt/neomutt/releases/download/$pkgname-$pkgver/$pkgname-$pkgver.tar.gz.sig")
sha256sums=('7fb76e99a9f23715ad772ad8f7008c6e2db05eed344817055176c76dbd60c1b5'
            'SKIP')
validpgpkeys=('86C2397270DD7A561263CA4E5FAF0A6EE7371805') # Richard Russon (flatcap) <rich@flatcap.org>

build() {
    cd "$pkgname-$pkgname-$pkgver"

    ./configure \
        --prefix=/usr \
        --sysconfdir=/etc \
        --with-gss=/usr \
        --with-ssl=/usr \
        --with-sasl=/usr \
        --disable-fcntl \
        --disable-idn \
        --disable-nls \
        --disable-pgp \
        --disable-smime \
        --bdb \
        --flock \
        --gdbm \
        --gnutls \
        --gpgme \
        --lmdb \
        --lua \
        --notmuch \
        --sasl
    
    make
}

package() {
    cd "$pkgname-$pkgname-$pkgver"
    make DESTDIR="${pkgdir}" install
}
