# Maintainer: Matt Aitchison <Matt.Aitchison@gliderlabs.com>
pkgname=openresty
pkgver=1.9.7.3
pkgrel=0
pkgdesc="A Fast and Scalable Web Platform by Extending NGINX with Lua"
pkgdesc="Entrypoint tools for elegant, programmable containers"
url="https://openresty.org"
arch="x86_64"
license="BSD"
pkgusers="nginx"
_grp_ngx="nginx"
_grp_www="www-data"
depends=""
depends_dev=""
makedepends="make gcc musl-dev pcre-dev openssl-dev zlib-dev ncurses-dev readline-dev curl perl"
install=""
subpackages=""
source="https://openresty.org/download/$pkgname-$pkgver.tar.gz"

_builddir="$srcdir"/$pkgname-$pkgver
build() {
	cd $_builddir
  ./configure \
		--prefix=/var/lib/$pkgname \
		--sbin-path=/usr/sbin/$pkgname \
		--conf-path=/etc/$pkgname/$pkgname.conf \
		--pid-path=/run/$pkgname/$pkgname.pid \
		--lock-path=/run/$pkgname/$pkgname.lock \
		--user=$pkgusers \
		--group=$_grp_ngx \
		--with-http_ssl_module \
		--with-luajit --with-pcre-jit \
			|| return 1

	make || return 1
}
package() {
	cd "$_builddir"
	make DESTDIR="${pkgdir}" install || return 1
}
# 
# package() {
# 	# install -Dm755 "$_builddir/bin/$pkgname" "$pkgdir/usr/bin/$pkgname"
# }

md5sums="33579b96a8c22bedee97eadfc99d9564  openresty-1.9.7.3.tar.gz"
sha256sums="3e4422576d11773a03264021ff7985cd2eeac3382b511ae3052e835210a9a69a  openresty-1.9.7.3.tar.gz"
sha512sums="6ccec824b8d32d70449988686df1531ec3a82fc7604776382ea0997cb25561abc3c3f58b83d1572b0b6350c05a1a007cc3465257ae3619a4286571a33cc745d2  openresty-1.9.7.3.tar.gz"
