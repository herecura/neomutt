pkgname=neomutt
pkgver=20160910
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
sha256sums=('cc1159c7210a706db765b7198ac53405d25e7577ff9e5cd2f1d062964213798b')

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

