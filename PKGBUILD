# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - This package contains a tool to convert Unified Robot Description Format (URDF) documents into COLLAborative Design Activity (COLLADA) documents."
url='http://ros.org/wiki/collada_urdf'

pkgname='ros-hydro-collada-urdf'
pkgver='1.10.20'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-urdfdom
  ros-hydro-resource-retriever
  ros-hydro-collada-parser
  ros-hydro-urdfdom-headers
  ros-hydro-roscpp
  ros-hydro-angles
  ros-hydro-catkin
  ros-hydro-tf
  ros-hydro-geometric-shapes
  ros-hydro-urdf
  ros-hydro-cmake-modules)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  assimp
  collada-dom)

ros_depends=(ros-hydro-urdfdom
  ros-hydro-resource-retriever
  ros-hydro-collada-parser
  ros-hydro-urdfdom-headers
  ros-hydro-roscpp
  ros-hydro-angles
  ros-hydro-tf
  ros-hydro-geometric-shapes
  ros-hydro-urdf)
depends=(${ros_depends[@]}
  assimp
  collada-dom)

_tag=release/hydro/collada_urdf/${pkgver}-${_pkgver_patch}
_dir=collada_urdf
source=("${_dir}"::"git+https://github.com/ros-gbp/robot_model-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
