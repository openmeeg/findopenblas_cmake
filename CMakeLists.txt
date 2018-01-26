cmake_minimum_required (VERSION 3.2)
project (CMakeHelloWorld VERSION 1.0 LANGUAGES CXX)

# Find the BLAS stuff
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

set(BLA_DEFINITIONS)

# user defined options for MKL

find_package(OpenBLAS REQUIRED)

if (OpenBLAS_FOUND)
    # We should agree on BLA/BLAS variables
    set(BLA_INCLUDE_DIR ${OpenBLAS_INCLUDE_DIRS})
    set(BLA_LIBRARIES ${OpenBLAS_LIBRARIES})
    set(BLA_DEFINITIONS USE_OPENBLAS)
endif()

message(STATUS "BLAS Libraries: ${BLA_LIBRARIES}")

# include the subdirectory containing our libs
add_subdirectory(Hello)
# include(Hello/CMakeLists.txt)

# indicate the entry point for the executable
add_executable(CMakeHelloWorld Hello HelloWorld.cpp)

# Indicate which libraries to include during the link process.
target_link_libraries(CMakeHelloWorld Hello ${BLA_LIBRARIES})

# install (TARGETS CMakeHelloWorld DESTINATION bin)
