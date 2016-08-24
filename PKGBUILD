pkgname=neomutt
pkgver=20160822
pkgrel=1
pkgdesc='Small but powerful text-based mail client'
url='http://www.neomutt.org/'
license=('GPL')
backup=('etc/Muttrc')
arch=('i686' 'x86_64')
makedepends=('libxslt' 'w3m')
depends=('gnupg' 'gpgme' 'krb5' 'libidn' 'libsasl' 'mime-types'
         'notmuch-runtime' 'openssl' 'gdbm')
conflicts=('mutt')
provides=('mutt')
replaces=('mutt-kz' 'mutt-patched')
source=("https://github.com/neomutt/neomutt/archive/neomutt-$pkgver.tar.gz")
sha256sums=('acbf21fefee787da4b0410c88cb444445ac9f02848afd96e0080d26e2d9440ea')

build() {
    cd "$pkgname-$pkgname-$pkgver"

    ./prepare \
        --prefix=/usr \
        --sysconfdir=/etc \
        --enable-compressed \
        --enable-fcntl \
        --enable-gpgme \
        --enable-hcache \
        --enable-imap \
        --enable-pop \
        --enable-smtp \
        --with-curses=/usr \
        --with-gss=/usr \
        --with-ssl=/usr \
        --with-idn \
        --with-regex \
        --with-sasl \
        --without-bdb \
        --without-qdbm \
        --enable-sidebar \
        --enable-nntp \
        --enable-notmuch

    make
}

package() {
    cd "$pkgname-$pkgname-$pkgver"
    make DESTDIR="${pkgdir}" install

    rm "${pkgdir}"/etc/mime.types{,.dist}
    install -D -m 644 contrib/gpg.rc "$pkgdir"/etc/Muttrc.gpg.dist
}

