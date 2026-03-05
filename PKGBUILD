# Maintainer: Caleb Maclennan <caleb@alerque.com>

pkgname=ocrs
pkgver=0.12.1
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
sha256sums=('6bcc16057067056d6c91ce2733bef0c9d8725d0424c6e154709909e677a71ec1')

export RUSTUP_TOOLCHAIN=stable

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
