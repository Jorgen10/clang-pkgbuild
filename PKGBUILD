pkgname=python-clang
pkgver=r478.bc1cddd
pkgrel=1
pkgdesc="Clang, the best bot in the world"
arch=('any')
url="https://github.com/maidnaut/clang"
license=('GPL-3.0-or-later')
makedepends=('python' 'git')
backup=('opt/python-clang/.env')
depends=('python')
install=python-clang.install
source=("$pkgname::git+https://github.com/maidnaut/clang.git" "python-clang.service" "requirements.txt")
sha256sums=('SKIP' 'c683c269359a37f699c47bf409d5cd7e8cb1fe1b0c352ccc5418032211489c48' '64a6afdf40f402c1309cb7b96eb0e9356883217773ef2f057fa9892d8fb37fa1')

pkgver() {
  cd "$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

package() {
  cd "$pkgname"

  install -d "$pkgdir/opt/python-clang"
  echo "BOT_TOKEN=" > "$pkgdir/opt/python-clang/.env"
  mv ./* "$pkgdir/opt/python-clang"

  install -Dm644 "../requirements.txt" "$pkgdir/opt/python-clang/requirements.txt"

  install -Dm644 "../python-clang.service" "$pkgdir/etc/systemd/system/python-clang.service"
}