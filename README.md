# conda-environments


## Generic setup on Mac OS

Brew package manager , install from website

    brew install gcc
    brew install cmake
    brew install git
    brew install git-lfs
    brew install gnupg
    brew install zsh
    brew install python
    brew install sphinx-doc


## Installing `conda` and `python`


### Installing our python libraries

## Installing `zgoubi`

## Installing `madx`

On MAC-OS temporarily defa
Clone the git repository :

git clone https://github.com/MethodicalAcceleratorDesign/MAD-X.git
mkdir madx-build
cd madx-build
cmake -DCMAKE_C_COMPILER=/usr/local/bin/gcc-9 -DCMAKE_CXX_COMPILER=/usr/local/bin/g++-9 -DCMAKE_Fortran_COMPILER=/usr/local/bin/gfortran -DCMAKE_OSX_ARCHITECTURES=x86_64 -DMADX_ONLINE=OFF -DMADX_INSTALL_DOC=OFF -DCMAKE_INSTALL_PREFIX=./install -DCMAKE_C_FLAGS="-fvisibility=protected" -DBUILD_SHARED_LIBS=ON ../MAD-X
make -j8
make install

This should produce MAD-X binary and libraries in the ./install directory.

Build CPYMAD:

git clone https://github.com/hibtc/cpymad
cd cpymad
MADXDIR=/PATH/TO/CMAKE_INSTALL_PREFIX SHARED=1 LIBRARY_PATH=/opt/X11/lib:$LIBRARY_PATH CC=gcc-9 CXX=g++-9 python setup.py build_ext -lblas -llapack
conda activate py37
python setup.py install



## Installing `root`

brew install root

## Installing `geant4`

brew install geant4 --with-system-clhep --with-gdml --with-qt --without-example


## Installing `bdsim`

 CMAKE_PREFIX_PATH=/usr/local/opt/flex:/usr/local/opt/bison:$CMAKE_PREFIX_PATH cmake ../bdsim


## Installing `freecad`

cmake \
  -DCMAKE_BUILD_TYPE="Release"   \
  -DBUILD_QT5=1                  \
  -DCMAKE_PREFIX_PATH="/usr/local/Cellar/qt/5.13.0/lib/cmake/"  \
  -DFREECAD_USE_EXTERNAL_KDL=1   \
  -DBUILD_FEM_NETGEN=1           \
  -DFREECAD_CREATE_MAC_APP=1     \
  -DCMAKE_INSTALL_PREFIX="./.."  \
  -DBoost_NO_BOOST_CMAKE:BOOL=ON \

## Installing `fluka` and `flair`

Local installation of FLUKA:

    –	git clone fluka
    –	make

Fluka and FLAIR in a Docker image:

    –	install docker from https://docker.com (docker Desktop)
    –	docker-fluka-flair in channel code-fluka
    –	brew install socat
    –	socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"
    –	docker build --tag centos-flukaflair .
    –	docker run -ti --rm -e DISPLAY=$(ipconfig getifaddr en0):0 -v /tmp/.X11-unix:/tmp/.X11-unix -v /Users/chernals/cernbox:/tmp/cernbox centos-flukaflair