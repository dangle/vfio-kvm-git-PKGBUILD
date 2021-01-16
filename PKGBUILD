# Packager: Melissa Nuño
# Maintainer: Melissa Nuño

pkgname=vfio-kvm-git
pkgver=1.0.0.r0.gc23b0fe
pkgrel=1
pkgdesc="A systemd service that send a D-Bus signal when a QEMU evdev hotkey is pressed."
arch=('any')
url='https://github.com/dangle/vfio-kvm'
license=('MIT')
depends=('python>=3.7' 'python-evdev' 'python-dbus-next')
makedepends=('git')
provides=(${pkgname%-*})
conflicts=(${pkgname%-*})
source=('git+https://github.com/dangle/vfio-kvm.git')
md5sums=('SKIP')

pkgver() {
  cd "${pkgname%-*}"
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

package() {
  cd "$srcdir/${pkgname%-*}"
  install -Dm644 "LICENSE" -t "${pkgdir}/usr/share/licenses/${pkgname}"
  install -Dm644 "config/dbus/vfio-kvm.xml" "${pkgdir}/etc/dbus-1/system.d/vfio-kvm.conf"
  install -Dm644 "config/systemd/vfio-kvm.service" -t "${pkgdir}/usr/lib/systemd/system"
  install -Dm755 "vfio-kvm.py" "${pkgdir}/usr/bin/vfio-kvm"
}
