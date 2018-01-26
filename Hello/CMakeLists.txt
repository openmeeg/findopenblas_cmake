add_library(Hello
  Speaker.h
  Speaker.cpp)

target_compile_definitions(Hello PUBLIC ${BLA_DEFINITIONS})

target_include_directories(Hello PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:include>  # <prefix>/include
    ${BLA_INCLUDE_DIR})

