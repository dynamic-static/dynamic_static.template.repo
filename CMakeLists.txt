
cmake_minimum_required(VERSION 3.17 FATAL_ERROR)
project(dynamic_static.placeholder)

################################################################################
# Dependencies
set(external "${CMAKE_CURRENT_LIST_DIR}/external/")
string(REPLACE "\\" "/" DYNAMIC_STATIC "$ENV{DYNAMIC_STATIC}")
include("${external}/dynamic_static.build.cmake")
include("${external}/dynamic_static.random.cmake")
include("${external}/dynamic_static.string.cmake")
include("${external}/dynamic_static.time.cmake")
list(APPEND linkLibraries
    dynamic_static.random
    dynamic_static.string
    dynamic_static.time
)

################################################################################
# Include files
set(includeDirectory "${CMAKE_CURRENT_LIST_DIR}/include/")
set(includePath "${includeDirectory}/dynamic_static/")
list(APPEND includeFiles
    "${includePath}/placeholder.hpp"
)

################################################################################
# Source files
set(sourcePath "${CMAKE_CURRENT_LIST_DIR}/source/dynamic_static/")
list(APPEND sourceFiles
    "${sourcePath}/placeholder.cpp"
)

################################################################################
# Target
dst_add_static_library(
    target ${CMAKE_PROJECT_NAME}
    includeDirectories PUBLIC "${includeDirectory}/"
    includeFiles "${includeFiles}"
    sourceFiles "${sourceFiles}"
)

################################################################################
# Tests
set(testsPath "${CMAKE_CURRENT_LIST_DIR}/tests/")
dst_add_target_test(
    target ${CMAKE_PROJECT_NAME}
    sourceFiles "${testsPath}/placeholder.tests.cpp"
)
