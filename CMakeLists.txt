cmake_minimum_required (VERSION 3.2)
project (CMakeHelloWorld VERSION 1.0)

# Find the BLAS stuff
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

set(BLA_DEFINITIONS)

# user defined options for MKL

find_package(OpenBLAS REQUIRED)

if (OpenBLAS_FOUND)
    include_directories(${OpenBLAS_INCLUDE_DIRS})
    set(BLAS_LIBRARIES ${OpenBLAS_LIBRARIES})
    set(BLA_DEFINITIONS USE_OPENBLAS)
endif()

message(STATUS "BLAS Libraries: ${BLAS_LIBRARIES}")

# include the subdirectory containing our libs
add_subdirectory(Hello)
include_directories(Hello)
# indicate the entry point for the executable
add_executable(CMakeHelloWorld Hello HelloWorld.cpp)

# Indicate which libraries to include during the link process.
target_link_libraries(CMakeHelloWorld Hello ${BLAS_LIBRARIES})

# install (TARGETS CMakeHelloWorld DESTINATION bin)
