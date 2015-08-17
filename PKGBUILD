# Maintainer: lilydjwg [ lilydjwg at gmail dot com ]
# Last changed: 2011-07-26 16:54

pkgname=python-greenlet-hg
pkgver=152
pkgrel=1
pkgdesc="python coroutine library"
license=("MIT")
url="https://bitbucket.org/ambroff/greenlet"
depends=('python')
arch=('i686' 'x86_64')
conflicts=(python-greenlet)
provides=(python-greenlet=0.3.1)

_hgroot="https://bitbucket.org/ambroff"
_hgrepo="greenlet"

fetch() {
  # update source
  cd $srcdir

  if [ -d ${_hgrepo} ]; then
    cd $srcdir/${_hgrepo}
    hg pull -u
    hg update ${_basename}
  else
    hg clone ${_hgroot}${_hgrepo} || return 1
    cd $srcdir/${_hgrepo}
    hg update ${_basename}
  fi

  msg "Mercurial checkout done or server timeout"
  msg "Starting make..."
}

build()
{
  cd "$srcdir/$_hgrepo"

  /usr/bin/python setup.py build || return 1
  /usr/bin/python setup.py install --root=$startdir/pkg
}

# vim:set ts=2 sw=2 et:
