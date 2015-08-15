# $Id:$
# Contributor: Balwinder S "bsd" Dheeman (bdheeman AT gmail.com)
# Maintainer: Balwinder S "bsd" Dheeman (bdheeman AT gmail.com)

pkgname=chromium-browser-ppa
_pkgname=${pkgname%-ppa}
_pkgver=svn20120105r116462
_pkgpre=18.0.997.0~
_pkgsuf=0ubuntu1~ucd1~natty
pkgver=18.0.997.0.116462
pkgrel=1
pkgdesc="The open-source project behind Google Chrome (Web/HTTP/FTP Browser)"
arch=('i686' 'x86_64')
url=https://launchpad.net/chromium-browser/
license=('custom:BSD')
depends=('alsa-lib' 'bzip2' 'gconf' 'gtk2' 'nss' 'libpng12' 'libxss' 'libxtst')
optdepends=('chromium-browser-inspector-ppa: for HTML/CSS development [AUR]'
    'chromium-browser-l10n-ppa: for additional languages pack [AUR]'
    'chromium-codecs-ffmpeg-extra-ppa: for viewing HTML5/H.264 videos [AUR]'
    'ttf-hannom-usong: Unicode Han and Nom (Chinese and Vietnamese) fonts [AUR]'
    'ttf-indic-otf: Unicode collection various (Indian) language fonts [extra]'
    'otf-ipafont: Unicode Gothic/sans and Mincho/serif (Japanese) fonts [AUR]'
    'lsb-release: An ArchLinux specific LSB Release/Version query tool [AUR]'
    'xdg-utils: for setting a default browser on desktop environments [extra]')
provides=("${_pkgname}")
conflicts=("${_pkgname}" 'chromium-browser-bin' "${_pkgname}-svn" 'chromium-os-bin' 'google-chrome-dev')
replaces=('chromium-browser-bin')
backup=("etc/${_pkgname}/default")
options=('emptydirs' '!strip')
install=install.sh

case "$CARCH" in
    i686|i[3-5]86)
	_bldarch='i386'
	md5sums=('7d40a93d0ee6d1f00f4ad9db8ed0479e');;
    x86_64|amd64)
	_bldarch='amd64'
	md5sums=('c687cdcee42344adad57c8234a45e515');;
    # The following should not happen; provided you're using 'makepkg' ;)
    *) error "Unknown or invalid CARCH=$CARCH"; exit 1
esac

_url=http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser
source=(${_url}/${_pkgname}_${_pkgpre}${_pkgver}-${_pkgsuf}_${_bldarch}.deb)

build() {
    msg2 "Extracting files..."
    cd "$srcdir"
    ar x ${_pkgname}_${_pkgpre}${_pkgver}-${_pkgsuf}_${_bldarch}.deb
    tar xf data.tar.lzma -C $pkgdir
    msg2 "Making it nice..."
    mkdir -p $pkgdir/usr/share/licenses/${pkgname}
    ln -s /usr/share/doc/${_pkgname}/copyright $pkgdir/usr/share/licenses/${pkgname}/LICENSE.txt
}

# vim:set ts=4 sw=4 et:
