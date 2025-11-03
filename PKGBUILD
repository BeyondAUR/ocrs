# Maintainer: Caleb Maclennan <caleb@alerque.com>

pkgname=ocrs
pkgver=0.11.0
pkgrel=1
pkgdesc='a modern OCR engine written in Rust'
arch=(x86_64)
url="https://github.com/robertknight/$pkgname"
license=(MIT Apache-2.0)
depends=(gcc-libs
         glibc)
makedepends=(rustup)
_tag="$pkgname-cli-v$pkgver"
_archive="$pkgname-$_tag"
source=("$url/archive/$_tag/$_archive.tar.gz")
sha256sums=('02848ee5fb16295e99f0ea0ecdbfc16863024798ff5dd88817556a812d4b3fe3')

export RUSTUP_TOOLCHAIN=nightly-2025-05-11

build() {
	cd "$_archive"
	cargo build --release --all-features
}

check() {
	cd "$_archive"
	cargo test --release --all-features
}

package() {
	cd "$_archive"
	install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
	install -D -m644 LICENSE-APACHE.txt -t "$pkgdir"/usr/share/licenses/$pkgname/
	install -D -m644 LICENSE-MIT.txt -t "$pkgdir"/usr/share/licenses/$pkgname/
}
