##################################################################################
# MIT License
#
# Copyright (c) 2024 Jose Alberto Granados
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
##################################################################################

cmake_minimum_required(VERSION 3.12)
project(examples VERSION 1.0.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CSS_STANDARD_REQUIRED True)

set(CPP_SOURCE_DIR ${PROJECT_SOURCE_DIR}/src)
set(GLOB_RECURSE CPP_SOURCES CONFIGURE_DEPENDS RELATIVE ${CPP_SOURCE_DIR} "${CPP_SOURCE_DIR}/*.cpp")

# your dependencies here...
# example:
#   set(LIB_SOURCE_DIR /path/to/lib/source)
#   find_library(LIB_NAME libname.so libname PATHS /path/to/lib/build)

foreach(EXAMPLE_CPP ${CPP_SOURCES})
    string(REPLACE ".cpp" "" EXAMPLE_NAME ${EXAMPLE_CPP})

    add_executable(${EXAMPLE_NAME} ${CPP_SOURCE_DIR}/${EXAMPLE_CPP})

    target_include_directories(${EXAMPLE_NAME} PUBLIC ${CPP_SOURCE_DIR}/include)

    # your dependencies here...
    # example:
    #   target_link_libraries(${EXAMPLE_NAME} ${LIB_NAME})
endforeach(EXAMPLE_CPP ${CPP_SOURCES})
