#Maintainer: Aeternus Atterratio <atterratio@gmail.com>

pkgname=django-sekizai-git
pkgver=20121021
pkgrel=2
pkgdesc="Django Template Blocks with extra functionality"
arch=('any')
url="https://github.com/ojii/django-sekizai"
license=('BSD')
depends=('python2' 'django')
makedepends=('git' 'python2-distribute')
provides=('django-sekizai')
conflicts=('django-sekizai')
replaces=('django-sekizai')

_gitroot="https://github.com/ojii/django-sekizai.git"
_gitname="django-sekizai"

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

}

package() {
  cd "$srcdir/$_gitname"
  python2 setup.py build || return 1
  python2 setup.py install --root=$pkgdir || return 1
  install -D -m644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
