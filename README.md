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
