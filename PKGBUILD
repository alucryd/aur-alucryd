# Maintainer: Florian Maunier <fmauneko@dissidence.ovh>
# Contributor: jtmb <packaging at technologicalwizardry dot com>
pkgbase=msbuild
pkgname=('msbuild' 'msbuild-sdkresolver')
pkgver=16.0+xamarinxplat.2019.04.08.19.19
pkgrel=3
arch=('x86_64')
makedepends=('libcurl-gnutls')
url="https://github.com/mono/msbuild"
license=('MIT')
source=("https://download.mono-project.com/sources/msbuild/msbuild-${pkgver}.tar.xz"
        'fix-install.patch')
sha256sums=('0d425603281ae84d3cf560ea4f9e2b2159e7764f71406035070a7fe27878ec49'
            '8780925e01d4e5bdf8f93c439fe92da7a64f14099b60382499b477a512b56dca')

prepare() {
    cd "${pkgname}-${pkgver%+*}"
    patch --forward --strip=1 --input="${srcdir}/fix-install.patch"
}

build() {
    cd "${pkgname}-${pkgver%+*}"
    make
    ./install-mono-prefix.sh "/usr" /p:StagingDir="${srcdir}/target/usr" /p:TargetMSBuildToolsVersion="15.0"
    find $srcdir/target/usr/lib/mono/ -name Microsoft.DiaSymReader.Native.*dll -delete
    find $srcdir/target/usr/lib/mono/ -name *.dylib -delete
}

package_msbuild() {
    pkgdesc="Xamarin implementation of the Microsoft build system"
    depends=('mono>=5.0.0')

    cp -dr --no-preserve='ownership' $srcdir/target/usr "${pkgdir}"
    rm -rf $pkgdir/usr/lib/mono/msbuild/15.0/bin/SdkResolvers/Microsoft.DotNet.MSBuildSdkResolver
}

package_msbuild-sdkresolver() {
    pkgdesc="Xamarin implementation of the Microsoft build system (SDK resolver)"
    depends=('msbuild')

    mkdir -p "${pkgdir}"/usr/lib/mono/msbuild/15.0/bin/SdkResolvers/
    cp -dr --no-preserve='ownership' $srcdir/target/usr/lib/mono/msbuild/15.0/bin/SdkResolvers/Microsoft.DotNet.MSBuildSdkResolver "${pkgdir}"/usr/lib/mono/msbuild/15.0/bin/SdkResolvers/
}
