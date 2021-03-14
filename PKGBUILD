# Maintainer: Christian Hesse <mail@eworm.de>
# Contributor: Aaron Fischer <mail@aaron-fischer.net>
# Contributor: Steven Allen <steven@stebalien.com>
# Contributor: trile7 at gmail dot com
# Contributor: Ernia <monghitri@aruba.it>

pkgname=yad
pkgver=8.0
pkgrel=2
pkgdesc='A fork of zenity - display graphical dialogs from shell scripts or command line'
url='https://github.com/v1cont/yad'
arch=('x86_64')
license=('GPL3')
depends=('gtk3' 'webkit2gtk' 'gtkspell3')
makedepends=('autoconf' 'automake' 'intltool')
source=("https://github.com/v1cont/yad/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.xz"
"yad-8.0-size-request.patch")
sha256sums=('5c9538b7f242de715249e9f7d30108c0706d23219b5b1bb85cfead6ae77abff3'
            'd7c94d0f046be3ef565ac1c45599d920d5d570f93d3ab5af49999845969fb6d7')

prepare() {
    cd "$pkgname-$pkgver"
  patch -d "${srcdir}/${pkgname}-${pkgver}" -p1 -i ../yad-8.0-size-request.patch
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  autoreconf -ivf
  intltoolize
  ./configure \
    --prefix=/usr \
    --enable-icon-browser \
    --enable-html \
    --enable-gio \
    --enable-spell \
    --enable-sourceview

  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  make DESTDIR="${pkgdir}" install
}

