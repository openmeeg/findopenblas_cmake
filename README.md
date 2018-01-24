[![Build status](https://travis-ci.org/openmeeg/findmkl_cmake.svg?branch=master)](https://travis-ci.org/openmeeg/findmkl_cmake/branches)
[![Build status](https://ci.appveyor.com/api/projects/status/0dfbalwmtix81it8?svg=true)](https://ci.appveyor.com/project/openmeegci/findmkl-cmake)

This repo provides FindOpenBLAS.cmake file, which can be used to configure a CMake project that needs OpenBLAS.
We basically took [this](https://github.com/jameskbride/cmake-hello-world) extremely simple C++ example,
modify the code to require OpenBLAS, provide CMake package finder for OpenBLAS and add all the Contineous Integration (CI) to test it against different scenarios. 

Tests are run on Mac, Linux and Windows, using both static or dynamic libraries.

### How to use this project ###
Actually you can use this project in whatever manner you like. But we think that there are two main ways to use this project:

1. Clone/Fork/Download the entire project and use it as your starting point. This has the advantage that travis and appveyor would be already configured, for you. The only step required to have CI up and running would be to activate your porject in those platforms.

2. Download [`FindOpenBLAS.cmake`](./cmake/FindOpenBLAS.cmake) and place it wherever is needed in your project.

### How to run this example ###
The best way to understand how to run a project (or install its dependencies) is always looking to CI's configuration ([.travis.yml](./.travis.yml) and [.appveyor.yml](./.appveyor.yml)). 
But as a summary, as this is an example of how to use OpenBLAS and CMake you'll need to install OpenBLAS and [download CMake](http://www.cmake.org/cmake/resources/software.html). If you are using an ubuntu, CMake can be install it via:
```bash
sudo apt-get install cmake
```
Once CMake and OpenBLAS have been installed navigate to the root of the project and issue the following commands:
```bash
mkdir build
cd build
cmake .. && cmake --build .
```
