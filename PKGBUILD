# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Your Name <k.sath214@gmail.com>
pkgname=nintenno-dwm
pkgver=6.2.r2.d7eff6d
pkgrel=1
pkgdesc="My Personal dwm build at https://github.com/KSatheeskumar21/nintenno-dwm"
arch=(x86_64)
url="https://github.com/KSatheeskumar21/nintenno-dwm"
license=('MIT')
groups=()
depends=(libx11 libxinerama nerd-fonts-source-code-pro ttf-jetbrains-mono ttf-joypixels picom nitrogen xfce4-clipman-plugin network-manager-applet dunst nintenno-dmenu nintenno-st alacritty)
makedepends=(make)
checkdepends=()
optdepends=()
provides=(dwm)
conflicts=()
replaces=(dwm)
backup=()
options=()
install=${pkgname}.install
changelog=
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

prepare() {
	cd "${_pkgname}"
	printf "6.2.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd nintenno-dwm
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd nintenno-dwm
	mkdir -p $pkgdir/opt/$pkgname
	cp -rf * $pkgdir/opt/$pkgname
	sudo make PREFIX=/usr DESTIR="$pkgdir" install
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/nintenno-dwm/LICENSE"
	install -Dm644 README "$pkgdir/usr/share/doc/nintenno-dwm/README"
	install -Dm644 "$srcdir/nintenno-dwm/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
}
