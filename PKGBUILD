# Maintainer: Kishore Satheeskumar <k.sath214@gmail.com>
pkgname=nintenno-dwm
pkgver=6.2.r7.2e63d31
pkgrel=1
pkgdesc="My Personal dwm build at https://github.com/KSatheeskumar21/nintenno-dwm"
arch=(x86_64)
url="https://github.com/KSatheeskumar21/nintenno-dwm"
license=('MIT')
groups=()
depends=(libx11 libxinerama freetype2 libxft-bgra-git nerd-fonts-source-code-pro ttf-jetbrains-mono ttf-joypixels picom nitrogen xfce4-clipman-plugin network-manager-applet dunst nintenno-dmenu nintenno-st alacritty)
makedepends=(make)
checkdepends=()
optdepends=(nintenno-surf)
provides=(dwm)
conflicts=(dwm)
replaces=()
backup=()
options=()
install=${pkgname}.install
changelog=
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
	cd "${_pkgname}"
	printf "6.2.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd nintenno-dwm
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETPYEINC=/usr/include/freetype2
}

package() {
	cd nintenno-dwm
	mkdir -p ${pkgdir}/opt/${pkgname}
	cp -rf * ${pkgdir}/opt/${pkgname}
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/nintenno-dwm/LICENSE"
	install -Dm644 README "${pkgdir}/usr/share/doc/nintenno-dwm/README"
	install -Dm644 "${srcdir}/nintenno-dwm/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
}
