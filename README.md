# mom6-cmake
CMake-compatible build for MOM6

## Example use on Gadi
Load the following modules:
- `cmake/3.24.2`
- `netcdf/4.7.3`
- `openmpi/4.1.4`
- `intel-compiler/2021.7.0`
- `python3/3.9.2`

First clone (recursively) https://github.com/angus-g/mom6-cmake and https://github.com/NOAA-GFDL/FMS.
```sh
git clone --recursive https://github.com/angus-g/mom6-cmake
git clone https://github.com/noaa-gfdl/fms
```

Then build with the install prefix set to the `mom6-cmake` directory:
```sh
cd fms
mkdir build && cd build
cmake -D32BIT=OFF -D64BIT=ON -DCMAKE_INSTALL_PREFIX="$(readlink -f ../..)/mom6-cmake/fms" ..
make
make install
```

Now build MOM6:
```sh
cd ../mom6-cmake
mkdir build && cd build
CMAKE_PREFIX_PATH="$(readlink -f ..)/fms" cmake -DCMAKE_BUILD_TYPE=Release ..
make
```
