pkgname=neomutt
pkgver=20171027
pkgrel=1
pkgdesc='Small but powerful text-based mail client'
url='http://www.neomutt.org/'
license=('GPL')
backup=('etc/Muttrc')
arch=('i686' 'x86_64')
depends=('openssl' 'gdbm' 'mime-types' 'libsasl' 'gnupg' 'gpgme' 'libidn' 'krb5' 'notmuch-runtime')
optdepends=('urlview: for url menu')
makedepends=('libxslt' 'w3m' 'gnupg')
conflicts=('mutt')
provides=('mutt')
replaces=('mutt-kz' 'mutt-patched')
source=("https://github.com/neomutt/neomutt/archive/neomutt-$pkgver.tar.gz")
sha256sums=('1b431b6b00bac5377c49f7dad3e32a36de48c55e48532a44f2fdd0c1d46d432a')

build() {
    cd "$pkgname-$pkgname-$pkgver"

    ./prepare \
        --prefix=/usr \
        --sysconfdir=/etc \
        --enable-pgp \
        --enable-gpgme \
        --enable-notmuch \
        --enable-pop \
        --enable-imap \
        --enable-smtp \
        --enable-hcache \
        --enable-sidebar \
        --enable-compressed \
        --with-gss=/usr \
        --with-ssl=/usr \
        --with-sasl \
        --with-curses=/usr \
        --with-regex \
        --with-idn \
        --with-gdbm \
        --enable-nntp \
        --enable-fcntl

    make
}

package() {
    cd "$pkgname-$pkgname-$pkgver"
    make DESTDIR="${pkgdir}" install
}

