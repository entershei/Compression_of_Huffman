cmake_minimum_required(VERSION 2.8)

project(compression_of_Huffman)

include_directories(.)

add_executable(Compression_of_Huffman main.cpp)
add_executable(Compression_of_Huffman_testing
        lib/compression.cpp
        lib/compression.h
        test/test.cpp
        gtest/gtest.h
        gtest/gtest-all.cc
        gtest/gtest_main.cc
        )

add_library(compression SHARED lib/compression.h lib/compression.cpp)

target_link_libraries(Compression_of_Huffman compression)
target_link_libraries(Compression_of_Huffman_testing compression -lpthread)

if (CMAKE_COMPILER_IS_GNUCC OR CMAKE_COMPILER_IS_GNUCXX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++17 -pedantic")
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -D_GLIBCXX_DEBUG")
    set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -march=native")
    set(CMAKE_CXX_OUTPUT_EXTENSION_REPLACE ON)
endif ()
