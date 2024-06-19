cmake_minimum_required(VERSION 3.20) 
project(matrix)

add_library(matrix_lib INTERFACE)
set_target_properties(matrix_lib PROPERTIES
    CXX_STANDARD 20
    CXX_STANDARD_REQUIRED ON
)
target_include_directories(matrix_lib INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}")

add_executable(matrix main.cpp)
target_compile_options(matrix PRIVATE -Wall -Wextra -pedantic -Werror)
target_link_libraries(matrix PRIVATE matrix_lib)
set_target_properties(matrix PROPERTIES
    CXX_STANDARD 20
    CXX_STANDARD_REQUIRED ON
)

install(TARGETS matrix DESTINATION bin)
set(CPACK_GENERATOR DEB)
set(CPACK_PACKAGE_VERSION_MAJOR ${PROJECT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR ${PROJECT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH ${PROJECT_VERSION_PATCH})
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "bayan application")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "My Corporation")
include(CPack)
