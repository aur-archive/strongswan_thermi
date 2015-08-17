# Maintainer: Thermi <noel@familie-kuntze.de>

pkgname=strongswan_thermi
pkgver=5.1.1
pkgrel=1
pkgdesc="open source IPsec implementation"
url='http://www.strongswan.org'
license=("GPL")
arch=('i686' 'x86_64')
depends=('curl' 'gmp' 'iproute2' 'openssl' 'sqlite')
conflicts=('openswan' 'strongswan')
options=(!libtool)
backup=(etc/ipsec.conf etc/strongswan.conf)
source=(https://download.strongswan.org/strongswan-${pkgver}.tar.bz2)
changelog='CHANGELOG'
md5sums=('e3af3d493d22286be3cd794533a8966a')

build() {
  cd ${srcdir}/strongswan-${pkgver}

  ./configure --prefix=/usr \
        --sbindir=/usr/bin \
        --sysconfdir=/etc \
        --libexecdir=/usr/lib \
        --with-ipsecdir=/usr/lib/strongswan \
        --enable-sqlite \
        --enable-openssl --enable-curl \
        --enable-sql --enable-attr-sql \
        --enable-farp --enable-dhcp \
        --enable-eap-sim --enable-eap-sim-file --enable-eap-simaka-pseudonym \
        --enable-eap-simaka-reauth --enable-eap-identity --enable-eap-md5 \
        --enable-eap-gtc --enable-eap-aka --enable-eap-aka-3gpp2 \
        --enable-eap-mschapv2 --enable-eap-radius --enable-xauth-eap \
        --enable-ha --enable-gcm --enable-ccm --enable-ctr --enable-unity \
        --enable-integrity-test --enable-load-tester --enable-test-vectors \
        --enable-af-alg --disable-ldap \
        --with-capabilities=libcap --enable-cmd
  make
}

package() {
  cd "${srcdir}/strongswan-${pkgver}"
  make DESTDIR=${pkgdir} install
}
