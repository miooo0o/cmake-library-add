cmake_minimum_required(VERSION 3.28)

if(DEFINED ENV{VCPKG_PATH})
    set(VCPKG_PATH $ENV{VCPKG_PATH})
    message(STATUS "Found VCPKG_PATH: ${VCPKG_PATH}")
else()
    message(FATAL_ERROR "VCPKG_PATH environment variable is not set")
endif()

set(CMAKE_TOOLCHAIN_FILE "${VCPKG_PATH}/scripts/buildsystems/vcpkg.cmake" CACHE STRING "vcpkg toolchain file")
message(STATUS "Using CMAKE_TOOLCHAIN_FILE: ${CMAKE_TOOLCHAIN_FILE}")

project(
        graphics
        VERSION 0.1
        DESCRIPTION "side project"
        LANGUAGES CXX
)
set(CMAKE_CXX_STANDARD 14)

add_subdirectory(src)