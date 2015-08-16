# Contributor: Lukas Jirkovsky <l.jirkovsky@gmail.com>
# Maintainer: caemir <benjamin@colard.info>

pkgname=josm-svn
pkgver=r7182
pkgrel=1
pkgdesc="An editor for OpenStreetMap written in Java."
arch=('any')
url="http://josm.openstreetmap.de/"
license=('GPL')
conflicts=('josm' 'josm-latest')
depends=('java-runtime')
makedepends=('subversion' 'apache-ant')
source=('josm::svn+http://josm.openstreetmap.de/svn/trunk'
	'josm.desktop'
	'josm.sh')
md5sums=('SKIP'
	 'e2b8c820100f3403a6cd10c1239d659a'
         'a497395e555e22c5e0412ebbab911737')
pkgver() {
  cd "$srcdir/josm"
  local ver="$(svnversion)"
  printf "r%s" "${ver//[[:alpha:]]}"
}

build() {
  cd "$srcdir/josm"
  . /etc/profile.d/apache-ant.sh
  ant clean dist
}
package() {
  cd "$srcdir/"

	install -D -m644 josm/dist/josm-custom.jar "$pkgdir/usr/share/java/josm/josm.jar"
	install -D -m644 josm.desktop "$pkgdir/usr/share/applications/josm.desktop"
	install -D -m755 josm.sh "$pkgdir/usr/bin/josm"
	install -D -m644 josm/images/logo.png "$pkgdir/usr/share/pixmaps/josm.png"
}
