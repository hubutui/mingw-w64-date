# Maintainer: Hu Butui <hot123tea123@gmail.com>

_realname=date
pkgbase=mingw-w64-${_realname}
pkgname=("${MINGW_PACKAGE_PREFIX}-${_realname}")
pkgver=3.0.1
pkgrel=1
pkgdesc="A date and time library based on the C++11/14/17 <chrono> header"
arch=('any')
mingw_arch=('mingw32' 'mingw64' 'ucrt64' 'clang64' 'clang32')
url="https://github.com/HowardHinnant/date"
license=('apache')
makedepends=("${MINGW_PACKAGE_PREFIX}-cmake")
source=("${_realname}-${pkgver}.tar.gz::https://github.com/HowardHinnant/date/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('7a390f200f0ccd207e8cff6757e04817c1a0aec3e327b006b7eb451c57ee3538')

build() {
  MSYS2_ARG_CONV_EXCL="-DCMAKE_INSTALL_PREFIX=" \
  ${MINGW_PREFIX}/bin/cmake \
    -B "${srcdir}/build-${MINGW_CHOST}" \
    -DCMAKE_INSTALL_PREFIX="${MINGW_PREFIX}" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_SYSTEM_PREFIX_PATH=${MINGW_PREFIX} \
    -DUSE_SYSTEM_TZ_DB=ON \
    -G'MSYS Makefiles' \
    -S ${_realname}-${pkgver}
  cmake --build "${srcdir}/build-${MINGW_CHOST}"
}

package() {
  DESTDIR="${pkgdir}" \
  ${MINGW_PREFIX}/bin/cmake.exe \
    --build "${srcdir}/build-${MINGW_CHOST}" \
    --target install
}
