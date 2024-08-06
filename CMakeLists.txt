cmake_minimum_required (VERSION 3.14)

project (shaderc)

set (LIBSHADERC_SOURCES "src/*.cpp")

add_subdirectory (glslc)
add_subdirectory (libshaderc_util)
