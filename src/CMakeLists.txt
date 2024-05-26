cmake_minimum_required(VERSION 3.28)
#add_compile_options(-Werror -Wall -Wextra -Wpedantic -Wconversion -Wsign-conversion -Wshadow -Wundef -Wunreachable-code -Wstrict-aliasing -Wnull-dereference -Wdouble-promotion -Wformat=2 -Wcast-qual -Wcast-align)
add_compile_options(-Werror -Wall -Wextra)

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
    # Additional flags for GCC
    add_compile_options(-Wuseless-cast)
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
    # Additional flags for Clang
    add_compile_options(-Weverything -Wno-c++98-compat -Wno-c++98-compat-pedantic -Wno-unused-macros -Wno-padded)
endif ()

find_package(imgui CONFIG REQUIRED)
find_package(directxtk CONFIG REQUIRED)
#find_package(directx-headers CONFIG REQUIRED)

file(GLOB_RECURSE SOURCES "*.cpp" "*.h")
add_executable(graphics ${SOURCES})
target_include_directories(graphics PRIVATE "${VCPKG_PATH}/installed/x64-windows/include")
target_link_libraries(graphics PRIVATE
        imgui::imgui
        Microsoft::DirectXTK
)