# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Jonathan Kotta <jpkotta@gmail.com>
# Contributor: paul2lv <paul2lv@gmail.com>
# Contributor: dtw <dibblethewrecker@gmail.com>

pkgname=foldingathome
pkgver=7.5.1
pkgrel=4
pkgdesc='A distributed computing project for simulating protein dynamics'
arch=(x86_64)
url=https://foldingathome.org/
license=(custom)
depends=(
  gcc-libs
  glibc
  zlib
)
optdepends=(
  'cuda: for folding with an NVIDIA GPU'
  'opencl-amd: for folding with a newer AMD GPU'
  'opencl-mesa: for folding with an older AMD GPU'
  'opencl-nvidia: for folding with an NVIDIA GPU'
)
backup=(etc/foldingathome/config.xml)
source=(
  https://download.foldingathome.org/releases/public/release/fahclient/debian-stable-64bit/v${pkgver%.*}/fahclient_${pkgver}-64bit-release.tar.bz2
  foldingathome.service
)
sha256sums=('69a2562a4bc30bf10e1954bedd8b96aaf57df7eafcfca828f29304fbbbc2521f'
            'a5c9eb3114afec305dddaf31ea91341d2628fdf0ac02b8769941f4c4f9bc6cc6')

package() {
  install -Dm 755 fahclient_${pkgver}-64bit-release/FAHClient -t "${pkgdir}"/usr/bin/
  install -Dm 755 fahclient_${pkgver}-64bit-release/FAHCoreWrapper -t "${pkgdir}"/usr/bin/
  install -Dm 644 fahclient_${pkgver}-64bit-release/CHANGELOG.md -t "${pkgdir}"/usr/share/doc/foldingathome/
  install -Dm 644 fahclient_${pkgver}-64bit-release/README.md -t "${pkgdir}"/usr/share/doc/foldingathome/
  install -Dm 644 fahclient_${pkgver}-64bit-release/copyright -t "${pkgdir}"/usr/share/licenses/foldingathome/
  install -Dm 644 fahclient_${pkgver}-64bit-release/sample-config.xml "${pkgdir}"/etc/foldingathome/config.xml
  install -Dm 644 foldingathome.service -t "${pkgdir}"/usr/lib/systemd/system/
}

# vim: ts=2 sw=2 et:
