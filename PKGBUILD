# Maintainer: Caleb Maclennan <caleb@alerque.com>

pkgname=ocrs
pkgver=0.10.2
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
sha256sums=('194d4dcd4b8e1af5597867a94e10655d3c6709b3c23f88953440be6c3c4ea009')

prepare() {
	rustup toolchain install nightly
}

build() {
	cd "$_archive"
	cargo +nightly update
	cargo +nightly build --release --all-features
}

check() {
	cd "$_archive"
	cargo +nightly test --release --all-features
}

package() {
	cd "$_archive"
	install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
	install -D -m644 LICENSE-APACHE.txt -t "$pkgdir"/usr/share/licenses/$pkgname/
	install -D -m644 LICENSE-MIT.txt -t "$pkgdir"/usr/share/licenses/$pkgname/
}
