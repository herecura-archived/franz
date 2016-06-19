pkgname=franz
pkgver=3.0.2
pkgrel=1
pkgdesc='A free messaging app for WhatsApp, Facebook Messenger, Telegram, Slack and more.'
arch=('i686' 'x86_64')
depends=('alsa-lib' 'gconf' 'gtk2' 'libnotify' 'libxtst' 'nss')
url='http://meetfranz.com/'
license=('custom')
_file_i686="Franz-linux-ia32-$pkgver.tgz"
_file_x86_64="Franz-linux-x64-$pkgver.tgz"
source=("$pkgname.desktop" "$pkgname.png")
source_i686=("https://github.com/imprecision/franz-app/releases/download/$pkgver/$_file_i686")
source_x86_64=("https://github.com/imprecision/franz-app/releases/download/$pkgver/$_file_x86_64")
sha256sums=('c63052b7ada73dbc984f55afc6d0ad937bf57ae5b0b41b560ef46937afeb81c5'
            '6e761371afadf155b8bc25e94fd7de371c16130a87338300e5800924916a7a28')
sha256sums_i686=('19015503b5fce1509649e036bdd21866c490bc237778f6729566edaa2cc942f7')
sha256sums_x86_64=('67f1f0b673e8b765e0dc15b11829ab7f0f3c83d284f70bbe8b74f7e322706a88')
noextract=("$_file_i686" "$_file_x86_64")

[[ "$CARCH" = "i686" ]] && _file="$_file_i686"
[[ "$CARCH" = "x86_64" ]] && _file="$_file_x86_64"

package() {
    install -d "$pkgdir"/{opt/$pkgname,usr/{bin,share/{licenses/$pkgname,pixmaps}}}
    bsdtar -xf "$srcdir/$_file" -C "$pkgdir/opt/$pkgname"
    ln -sf /opt/$pkgname/Franz "$pkgdir/usr/bin/$pkgname"

    install -Dm644 "$srcdir/$pkgname.png" "$pkgdir/usr/share/pixmaps/franz.png"

    install -Dm644 "$pkgdir/opt/$pkgname/LICENSE" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    install -Dm644 "$pkgdir/opt/$pkgname/LICENSES.chromium.html" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSES.chromium.html"

    install -Dm644 "$srcdir/$pkgname.desktop" \
        "$pkgdir/usr/share/applications/$pkgname.desktop"

    # fix ownership
    chown root:root -R "$pkgdir/opt/$pkgname"

    # clean unneeded resources
    rm -rf "$pkgdir/opt/$pkgname/resources/app.asar.unpacked/node_modules"
}
