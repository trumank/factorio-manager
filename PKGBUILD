# Maintainer: Truman Kilen <t@kilen.me>
pkgname=factorio-manager
pkgver=0.0.1
pkgrel=1
pkgdesc="Scripts for managing simultaneous factorio servers"
arch=('x86_64')
license=('GPL')

package() {
  cp -r . "${pkgdir}"

  chgrp -R 258 "${pkgdir}"/etc/factorio-manager
}

optdepends=('mcrcon: RCON shell')
