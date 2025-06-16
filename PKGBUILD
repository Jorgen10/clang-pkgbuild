pkgname=python-clang-git
pkgver=r494.28f223f
pkgrel=1
pkgdesc="Clang, the best bot in the world"
arch=('any')
_repo='maidnaut'
url="https://github.com/$_repo/clang"
license=('GPL-3.0-or-later')
makedepends=('python' 'git')
backup=('var/lib/python-clang')
depends=('python')
install=python-clang.install
source=(
  "$pkgname::git+https://github.com/$_repo/clang.git"
  "python-clang.service"
  "requirements.txt"
  "python-clang"
)
sha256sums=(
  'SKIP'
  '0f26c509e3c32d8915e6c4bbf4548efbae0f9472daba939c18e044643da4c8c9'
  '64a6afdf40f402c1309cb7b96eb0e9356883217773ef2f057fa9892d8fb37fa1'
  '400f0f346dbf2f354b4fb0bb39031772660130c724bf3a6e1f6d164e639ba609'
)

pkgver() {
  cd "$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

package() {
  cd "$pkgname"

  install -d "$pkgdir/usr/share/python-clang"
  mv ./* "$pkgdir/usr/share/python-clang"

  install -Dm644 "../requirements.txt" "$pkgdir/usr/share/python-clang/requirements.txt"

  install -d "$pkgdir/var/lib/python-clang"
  echo "BOT_TOKEN=" > "$pkgdir/var/lib/python-clang/.env"

  install -Dm644 "../python-clang.service" "$pkgdir/etc/systemd/system/python-clang.service"

  install -Dm755 "../python-clang" "$pkgdir/usr/bin/python-clang"
  chmod +x "$pkgdir/usr/bin/python-clang"
}