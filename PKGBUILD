# Contributor: Jonas Heinrich <onny@project-insanity.org>
# Maintainer: Jonas Heinrich <onny@project-insanity.org>

# ToDo:
# - useradd hlds to postinst
# - chown hlds /opt/hlds
# - steam won't update itself, needs working dir /opt/hlds
# - make all settings in /etc/conf.d/hlds work

pkgname=hlds
pkgver=50
pkgrel=3
pkgdesc="Valve Half-Life 1 and Counter-Strike 1.6 dedicated server"
arch=('i686' 'x86_64')
url="http://steampowered.com"
license=('nonfree')
if [ "${CARCH}" = "x86_64" ]; then
    depends=('lib32-gcc-libs')
fi
source=("http://www.steampowered.com/download/hldsupdatetool.bin"
        'hlds.service'
        'hlds')
install=hlds.install
sha512sums=('6cb841109167ef76c604c8ae74b38471516fb815af5365ceeb172fd76aac149ae363134ccd3a6ceee2ef8fd29b0ce803f3d2b71ef2ac5de5d6f4e1cf8912e3ca'
            '0c00e5644a477e3700a309c52125a6968f6d1080bf6804c91fd39f40ba891d294cbd594fef007a6517c3893260fc63dc4791568a1d744e166e2659496e5dfb65'
            '6a62b719f9adde2c0325fe38e54868b9fb4235d37bc450b039b1f0704e73add495d84b820731b1c003cfa7c7e44611ec205f675c92d61ebba628480bf532e121')
build() {
    cd ${srcdir}
    chmod a+x hldsupdatetool.bin
    echo "yes" | ./hldsupdatetool.bin
}
package () {
    cd ${srcdir}
    # Installing binary
    install -Dm 755 "${srcdir}/steam" "${pkgdir}/opt/hlds/steam"
    # Installing service file
    install -Dm 644 "${srcdir}/hlds.service" "${pkgdir}/usr/lib/systemd/system/hlds.service"
    # Installing configuration file
    install -Dm 644 "${srcdir}/hlds" "${pkgdir}/etc/conf.d/hlds"
}

# vim:set ts=4 sw=4 et:
