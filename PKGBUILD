pkgname=python-clang
pkgver=r543.ddfef89
pkgrel=1
pkgdesc="Clang, the best bot in the world"
arch=('any')
_repo='maidnaut'
url="https://github.com/$_repo/clang"
license=('GPL-3.0-or-later')
makedepends=('python' 'git')
provides=('python-clang')
replaces=('python-clang-git')
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
  '49ae5800eaab574f0bf0fa2f85458c27e3193392c3f1140e2c46a5f775157275'
)

pkgver() {
  cd "$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

package() {
  cd "$pkgname"

  install -Dm644 LICENSE.md "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  install -d "$pkgdir/usr/share/python-clang"
  mv ./* "$pkgdir/usr/share/python-clang"

  install -Dm644 "../requirements.txt" "$pkgdir/usr/share/python-clang/requirements.txt"

  install -d "$pkgdir/var/lib/python-clang"
  echo "BOT_TOKEN=" > "$pkgdir/var/lib/python-clang/.env"

  install -Dm644 "../python-clang.service" "$pkgdir/etc/systemd/system/python-clang.service"

  install -Dm755 "../python-clang" "$pkgdir/usr/bin/python-clang"
  chmod +x "$pkgdir/usr/bin/python-clang"
}
