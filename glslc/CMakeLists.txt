# Copyright 2020 The Shaderc Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

find_package(Threads)

add_library(glslc STATIC
  src/file_compiler.cc
  src/file_compiler.h
  src/file.cc
  src/file.h
  src/file_includer.cc
  src/file_includer.h
  src/resource_parse.h
  src/resource_parse.cc
  src/shader_stage.cc
  src/shader_stage.h
  src/dependency_info.cc
  src/dependency_info.h
)

target_include_directories(glslc PUBLIC ${glslang_SOURCE_DIR})

target_link_libraries(glslc PRIVATE
  glslang SPIRV    # Glslang libraries
  $<$<BOOL:${SHADERC_ENABLE_WGSL_OUTPUT}>:libtint>      # Tint libraries, optional
  shaderc_util                                  # internal Shaderc libraries
  ${CMAKE_THREAD_LIBS_INIT})

