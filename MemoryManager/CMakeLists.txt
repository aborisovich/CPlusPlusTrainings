#
# Copyright(c) 2023 Andrey Borisovich. All rights reserved.
#
# SPDX-License-Identifier: Apache-2.0
#

cmake_minimum_required (VERSION 3.23)

project(MemoryManager DESCRIPTION "Training project for managing memory" LANGUAGES CXX)

add_executable(MemoryMngExec)
set_target_properties(MemoryMngExec PROPERTIES OUTPUT_NAME MemoryManager)
set_target_properties(MemoryMngExec PROPERTIES CXX_STANDARD 20)

add_library(MemoryMngSources INTERFACE)

add_subdirectory(include)
add_subdirectory(src)

enable_testing()
add_subdirectory(test)

target_link_libraries(MemoryMngExec PRIVATE MemoryMngSources)
