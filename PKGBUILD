#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com>, Guillaume Horel <guillaume.horel@gmail.com> and William Turner <willtur.will@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-fontparts/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-fontparts/discussions>

_langname="python"
_relname="fontMath"
_pacname="fontmath"

pkgname="${_langname}-${_pacname}"
pkgver=0.9.2
pkgrel=1
pkgdesc="A collection of objects that implement fast font, glyph, etc. math"
arch=(
  "any"
)
url="https://github.com/robotools/fontmath"
license=(
  "MIT"
)
depends=(
  "python-fonttools"
)
checkdepends=(
  "python-pytest"
)
makedepends=(
  "python-build"
  "python-installer"
  "python-setuptools-scm"
  "python-wheel"
)
_zipname="$_relname-$pkgver"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/$_relname/$_zipname.zip"
)
sha512sums=(
  "34a5553cba4a18b5255e99b95971e891b0851aecbec5a31e705542087ff50b422d9c247fb35a4dd70f66afd32fb0f6d2d958195595f137c1e4f9250dfc29abc7"
)

build() {

  cd "$_zipname"

  python -m build -wn
}

check() {

  cd "$_zipname"

  PYTHONPATH=Lib pytest Lib/fontMath/test
}

package() {

  cd "$_zipname"

  python -m installer -d "$pkgdir" dist/*.whl

  install -Dm0644 -t "$pkgdir/usr/share/licenses/$pkgname/" License.txt
}
