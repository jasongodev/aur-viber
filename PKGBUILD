# Maintainer: Jason Go <jasongo@jasongo.net>
# Contributor: Sandor Nagy <sandor[dot]nagy[at]kdemail[dot]net>
# Contributor: Mladen Pejaković <pejakm[at]autistici[dot]org>
# Contributor: Morealaz <morealaz@gmail.com>
# Contributor: Lev Lybin <lev.lybin@gmail.com>
# Contributor: Özgür Sarıer <ozgursarier1011601115[at]gmail[dot]com>

pkgname=viber
pkgver=27.3.0.2
pkgrel=4
pkgdesc="Free and secure calls and messages to anyone, anywhere, on any device and network, in any country!"
arch=('x86_64')
url='https://www.viber.com'
license=('LicenseRef-Viber-TOS')
depends=(
  'libxml2-legacy'
  'libxslt'
  'libxss'
  'qt6-multimedia'
)
optdepends=(
  'firefox: To open external links and media'
  'epiphany: To open external links and media'
  'konqueror: To open external links and media'
  'gnome-shell-extension-appindicator: To show tray icon in GNOME'
)
conflicts=('viber')
options=('!debug' '!strip')
source=(
  "viber-$pkgver-$pkgrel.deb::https://download.cdn.viber.com/cdn/desktop/Linux/viber.deb"
  'https://www.viber.com/app/uploads/Viber-Terms-of-Service-EN-March-2026.pdf'
)
b2sums=('12dc832a8ae7934b1bcb7d0d9ea702159dbaf1f1f4b91ddf00920a01ca8c34cd7d522e7b824c60413cdb97003b929ade91e7aa47feef7804497b140ae4a25d5f'
        '7a935c23873efaf903fa686c74a5a9ade31c29c8dee54f4d8f98742ffd3624ff203bd681b7ae525b2118e74680edf471b9ac14ac6cd2b2f07b13dc5960600c92')

prepare() {
  bsdtar -xf data.tar.xz -C ./
}

package() {
  # Link Viber binary
  install -dm755 "$pkgdir/usr/bin/"
  ln -s /opt/viber/Viber "$pkgdir/usr/bin/viber"

  # Copy all deb files
  cp -dr --no-preserve=ownership {opt,usr} "$pkgdir"

  # Copy Viber.svg to viber.svg
  cp "$pkgdir/usr/share/icons/hicolor/scalable/apps/Viber.svg" "$pkgdir/usr/share/icons/hicolor/scalable/apps/viber.svg"

  # Copy updated license
  install -Dm644 -t "$pkgdir/usr/share/licenses/viber/" Viber-Terms-of-Service-EN-March-2026.pdf
}
