# Script generated with Bloom
pkgdesc="ROS - The raspigibbon_ros package"
url='http://github.com/rt-net/RaspberryPiGibbon/wiki'

pkgname='ros-kinetic-raspigibbon-ros'
pkgver='0.2.1_1'
pkgrel=1
arch=('any')
license=('MIT'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-futaba-serial-servo'
'ros-kinetic-raspigibbon-bringup'
'ros-kinetic-raspigibbon-description'
'ros-kinetic-raspigibbon-msgs'
)

conflicts=()
replaces=()

_dir=raspigibbon_ros
source=()
md5sums=()

prepare() {
    cp -R $startdir/raspigibbon_ros $srcdir/raspigibbon_ros
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

