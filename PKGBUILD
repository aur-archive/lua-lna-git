# Maintainer: Lucas Hermann Negri <lucashnegri@gmail.com>

_pkg=lua-lna
pkgname=$_pkg-git
pkgver=20140425
pkgrel=1
pkgdesc="Provides matrices, linear algebra, complex numbers, and other math goodies for luajit."
arch=(any)
url="http://oproj.tuxfamily.org" 
depends=('luajit>=2.0.3' 'lapack' 'lua-kiss-git')
optdepends=('lua-gnuplot-git: used in the examples')
license=('MIT')
provides=("$_pkg")
conflicts=("$_pkg")

_gitroot=https://lucashnegri@bitbucket.org/lucashnegri/lna.git
_gitname=$_pkg

build() { 
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"
  mkdir -p "$pkgdir/usr/share/lua/5.1/"
  cp -r lna "$pkgdir/usr/share/lua/5.1/"
  cp -r doc "$pkgdir/usr/share/lua/5.1/lna/"
  mkdir -p "$pkgdir/usr/share/licenses/$_pkg/"
  cp COPYRIGHT "$pkgdir/usr/share/licenses/$_pkg/"
}
