# Maintainer: Gimmeapill <gimmeapill at gmail dot com>

pkgname=mixxx1.10-bzr
pkgver=3110
pkgrel=5
pkgdesc="Digital DJ mixing software. Branch 1.10 (stable) from bzr with cpu optimization enabled"
arch=('i686' 'x86_64')
url="http://www.mixxx.org/"
license=('GPL2')
depends=('libid3tag' 'libmad' 'portaudio' 'qt4' 'qtwebkit' 'libogg' 'libvorbis' 'libsndfile' 'taglib' 'portmidi')
makedepends=('bzr' 'scons>=0.98' 'pkgconfig>=0.15.0')
optdepends=('faad2: M4A support' 
			'mp4v2: M4A support' 
			'libshout: Shoutcast support')
provides=(mixxx)
conflicts=(mixxx mixxx-bzr mixxx1.8-bzr mixxx1.9-bzr)

_bzrmod=mixxx
_bzrtrunk=lp:${_bzrmod}/1.10

build() {
  cd ${srcdir}

  msg "Connecting to the server...."

  if [ ! -d ./${_bzrmod} ]; then
    bzr co ${_bzrtrunk} ${_bzrmod}
  else
    bzr up ${_bzrmod}
    cd ${_bzrmod}
  fi

  msg "BZR checkout done or server timeout"
  msg "Starting make..."

  cd "${srcdir}/${_bzrmod}/${_bzrmod}"

  scons qtdir=/usr/lib/qt4 prefix=/usr install_root=$pkgdir/usr tuned=1
  scons qtdir=/usr/lib/qt4 prefix=/usr install_root=$pkgdir/usr install
}
