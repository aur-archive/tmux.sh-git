# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=tmux.sh-git
pkgver=20150505
pkgrel=1
pkgdesc="Enable two tmux clients to connect and switch windows independently from each other, like GNU screen"
arch=('any')
depends=('tmux')
makedepends=('git')
url="https://github.com/bsandrow/tmux.sh"
license=('MIT')
source=(${pkgname%-git}::git+https://github.com/bsandrow/tmux.sh)
sha256sums=('SKIP')
provides=('tmux.sh')
conflicts=('tmux.sh')

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing documentation...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/tmux.sh/README.md"

  msg 'Installing executable...'
  install -Dm 755 tmux.sh "$pkgdir/usr/bin/tmux.sh"

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
  find "$pkgdir" -type f -name .gitignore -exec rm -r '{}' +
}
