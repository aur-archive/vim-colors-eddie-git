# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-colors-eddie-git
pkgver=20120220
pkgrel=1
pkgdesc="A dark pastel colorscheme my friend spent too much time on"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/mattsacks/vim-eddie"
license=('custom:vim')
source=(${pkgname%-git}::git+https://github.com/mattsacks/vim-eddie)
sha256sums=('SKIP')
provides=('vim-colors-eddie')
conflicts=('vim-colors-eddie')

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/vim-colors-eddie/README.md"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in colors; do
    cp -R $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
