#
# Copyright(c) 2023 Andrey Borisovich. All rights reserved.
#
# SPDX-License-Identifier: Apache-2.0
#

include(FetchContent)
FetchContent_Declare(
	googletest
	GIT_REPOSITORY https://github.com/google/googletest.git
	GIT_TAG release-1.12.1)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

add_executable(MemoryMngUT)
set_target_properties(MemoryMngUT PROPERTIES CXX_STANDARD 20)
target_link_libraries(MemoryMngUT PRIVATE MemoryMngSources)

add_subdirectory(include)
add_subdirectory(src)

target_link_libraries(MemoryMngUT PRIVATE gtest gtest_main gmock)

include(GoogleTest)
gtest_discover_tests(MemoryMngUT)
