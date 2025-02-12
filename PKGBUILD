# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer: David Runge <dvzrv@archlinux.org>

_py="python"
_pkg="annotated-types"
pkgname="${_py}-${_pkg}"
pkgver=0.7.0
pkgrel=2
_pkgdesc=(
  "Reusable constraint types"
  "to use with typing.Annotated"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="${_pkg}"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}"
)
makedepends=(
  "${_py}-build"
  "${_py}-hatchling"
  "${_py}-installer"
)
checkdepends=(
  "${_py}-pytest"
  "${_py}-pytest-mock"
  "${_py}-pytest-sugar"
)
source=(
  "${_pkg}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz"
)
sha512sums=(
  '1cd43119f9127bcf68929a53158a91cef94d16b7bae3647b830899089b05bb66070ca4ac052e2a0b2fadbe567bca01d7773006568382034b3fbe20678d5fdc9c'
)
b2sums=(
  '198587003482dc9169fa9bec586f64860ba69723e88dcbf38ae470b89484b37cc020ba8a810704361f286e56f3d05b8f0188547573137e705833a0b57d744ed1'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  pytest \
    -vv
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    "dist/"*".whl"
  install \
    -vDm644 \
    "LICENSE" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
  install \
    -vDm644 \
    "README.md" \
    -t \
    "${pkgdir}/usr/share/doc/${pkgname}/"
}
