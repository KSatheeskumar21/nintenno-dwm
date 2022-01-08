# Maintainer: Kishore Satheeskumar <k.sath214@gmail.com>
pkgname=nintenno-dwm
pkgver=6.2.r18.f805525
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
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
  cd "${_pkgname}"
  printf "6.2.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  echo "####################"
  echo "Pkg dir: ${pkgdir}"
  echo "####################"
  printf "\n"
  echo "####################"
  echo "src dir: ${srcdir}"
  echo "####################"
}

build() {
  cd nintenno-dwm
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  # cd "$srcdir/$pkgname"
  cd nintenno-dwm
  echo "Making directories and copying files"
  mkdir -p "${pkgdir}"/opt/${pkgname}
  cp -rf * "${pkgdir}"/opt/${pkgname}
  echo -e "Installing"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  echo -e "Copying LICENSE"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  echo -e "Copying README"
  install -Dm644 README.org "${pkgdir}/usr/share/doc/${pkgname}/README.org"
  echo -e "Copying desktop files"
  mkdir -p "${pkgdir}/usr/share/xsessions/"
  install -Dm644 "${srcdir}/nintenno-dwm/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
}
