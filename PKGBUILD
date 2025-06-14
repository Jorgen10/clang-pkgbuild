pkgname=python-clang
pkgver=1.0
pkgrel=1
pkgdesc="Clang, the best bot in the world"
arch=('any')
url="https://github.com/maidnaut/clang"
license=('GPL-3.0-or-later')
makedepends=('python' 'git')
depends=('python')
install=python-clang.install
source=("$pkgname::git+https://github.com/maidnaut/clang.git" "python-clang.service" "requirements.txt")
sha256sums=('SKIP' 'SKIP' 'SKIP')

package() {
  cd "$pkgname"

  install -d "$pkgdir/opt/python-clang"
  echo "BOT_TOKEN=" > "$pkgdir/opt/python-clang/.env"
  mv ./* "$pkgdir/opt/python-clang"

  install -Dm644 "../requirements.txt" "$pkgdir/opt/python-clang/requirements.txt"

  install -Dm644 "../python-clang.service" "$pkgdir/etc/systemd/system/python-clang.service"
}