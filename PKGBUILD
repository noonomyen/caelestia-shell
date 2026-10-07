# Reference: https://aur.archlinux.org/packages/caelestia-shell

pkgname='caelestia-shell'
pkgver=2.5.0.patch1
pkgrel=1
pkgdesc='The desktop shell for the Caelestia dotfiles (patched by noonomyen)'
arch=('x86_64' 'aarch64')
url='https://github.com/noonomyen/caelestia-shell/tree/patch/2.5.0'
license=('GPL-3.0-only')
depends=(
    'caelestia-cli'
    'quickshell-git'
    'glibc'
    'gcc-libs'

    # Brightness
    'ddcutil'
    'brightnessctl'

    # Services
    'libcava'
    'networkmanager'
    'lm_sensors'
    'aubio'
    'libpipewire'
    'libqalculate'
    'power-profiles-daemon'

    # Fonts
    'ttf-material-symbols-variable'
    'ttf-rubik-vf'
    'ttf-cascadia-code-nerd'

    # Qt modules
    'qt6-base'
    'qt6-declarative'
    'qt6-imageformats'
    'qt6-m3shapes-git'

    # Extra functionality
    'swappy'
    'fish'
    'bash'
)
optdepends=(
    'asdbctl: controlling the brightness of Apple Studio Displays'
    'fprintd: fingerprint unlock for the lock screen'
    'howdy-next: face unlock for the lock screen'
)
makedepends=('cmake' 'ninja' 'qt6-shadertools' 'git')
provides=($pkgname)
conflicts=($pkgname-git)

_repopath="${LOCAL_REPO:-${startdir}}"
source=("$pkgname::git+file://${_repopath}#branch=patch/2.5.0")
sha256sums=('SKIP')

build() {
    cd "${srcdir}/${pkgname}"

    cmake -B build -G Ninja \
        -DCMAKE_BUILD_TYPE=RelWithDebInfo \
        -DCMAKE_INSTALL_PREFIX=/ \
        -DVERSION="${pkgver%.patch*}" \
        -DGIT_REVISION="$(git rev-parse HEAD)" \
        -DDISTRIBUTOR="noonomyen patch"
    cmake --build build
}

package() {
    cd "${srcdir}/${pkgname}"

    DESTDIR="$pkgdir" cmake --install build
    install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
