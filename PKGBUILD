# Maintainer: Giancarlo Razzolini <grazzolini@archlinux.org>
pkgname=mkinitcpio-dropbear
pkgver=0.0.3
pkgrel=5
pkgdesc="Archlinux mkinitcpio hook to install and enable the dropbear daemon in early userspace"
arch=('any')
url="https://github.com/grazzolini/mkinitcpio-dropbear"
license=('GPL3')
depends=('dropbear' 'psmisc')
optdepends=('openssh: Allows the use of the same host keys used for normal access' 'mkinitcpio-netconf: Network interface configuration' 'mkinitcpio-ppp: PPP interface configuration')
#conflicts=('mkinitcpio-tinyssh')
#install=$pkgname.install
source=("${pkgname}-${pkgver}.tar.gz::$url/archive/v$pkgver.tar.gz" "mkinitcpio-dropbear-dss-fix.patch" "mkinitcpio-dropbear-allow-port-forward.patch")
changelog='ChangeLog'
sha512sums=('65d9d794411dc9da03d900655b748cdda72ad39f4b0188a25c1521ed656d9c92bbbf248b09e8eb7f345839001944fc56c10e1c1fe123a73732fea8ffb6fb78d4'
            '54dfe255597713b2b2ffcddbc7d788e28bb56eeb707e7b45b9e1826d7786412c293b372d60361d86a106acd97e4a03a83219030ddfa826b267b35adc5cbaa067'
            'dde348f99d920bf36f4a53b87600b1472f2d1d0aef0199c47bd452cfd9d725275af91d0dcee8f3d87cd437257804a13c7f4b180a819b5506a0f53cd82f54903d')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  patch -p1 < "$srcdir/mkinitcpio-dropbear-dss-fix.patch"
  patch -p1 < "$srcdir/mkinitcpio-dropbear-allow-port-forward.patch"
}

package() {
  install -Dm644 "$srcdir/$pkgname-$pkgver/dropbear_hook"      "$pkgdir/usr/lib/initcpio/hooks/dropbear"
  install -Dm644 "$srcdir/$pkgname-$pkgver/dropbear_install"   "$pkgdir/usr/lib/initcpio/install/dropbear"
  install -Dm644 "$srcdir/$pkgname-$pkgver/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
