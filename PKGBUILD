# Maintainer : SpepS <dreamspepser at yahoo dot it>
# Contributor: Shinlun Hsieh <yngwiexx@yahoo.com.tw>
# Contributor: Stefan Husmann <stefan-husmann@t-online.de>
# Contributor: farid abdelnour <farid at archlinux-br.org>

_name=alsamodular
pkgname=ams
pkgver=2.0.1
pkgrel=3
pkgdesc="Alsa Modular Synth is a realtime modular synthesizer and effect processor"
arch=('i686' 'x86_64')
url="http://alsamodular.sourceforge.net/"
license=('GPL')
depends=('qt' 'clalsadrv' 'ladspa' 'jack')
makedepends=('fftw')
optdepends=('amb-plugins: ambisonic plugins'
            'mcp-plugins: phaser, chorus and moog vcf plugins'
            'rev-plugins: reverb plugins'
            'swh-plugins: Steve Harris plugins'
            'vco-plugins: oscillator plugins'
            'fil-plugins: equaliser plugins'
            'tap-plugins: toms audio plugins'
            'cmt: Computer Music Toolkit plugins'
            'blop: bandlimited oscillator plugins'
            'pvoc: phase-vocoding plugins'
            'caps: the C* audio plugins')
install="$pkgname.install"
source=("http://downloads.sourceforge.net/project/$_name/$_name/$pkgver/$pkgname-$pkgver.tar.bz2"
        "$pkgname.desktop" "$pkgname.png")
md5sums=('0d41bd5aac066aa98be45fd7ab12d35f'
         'ffa277cffd52254f0297cbc2f200767e'
         '0349171d5431f1c6e56085f080eb8c68')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # DSO link flag
  export LIBS=" -ldl"

  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR=$pkgdir/ install

  # desktop file
  install -Dm644 ../$pkgname.desktop \
    "$pkgdir/usr/share/applications/$pkgname.desktop"

  # icon
  install -Dm644 ../$pkgname.png \
    "$pkgdir/usr/share/pixmaps/$pkgname.png"
}
