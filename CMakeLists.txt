cmake_minimum_required(VERSION 3.11)

project (FetchContent_lib_a)

include(FetchContent)

FetchContent_Declare(FetchContent_libb
    GIT_REPOSITORY https://github.com/cmaketest/FetchContent_libb.git
)

FetchContent_GetProperties(FetchContent_libb)
string(TOLOWER "FetchContent_libb" lc_libb_Name)
if(NOT ${lc_libb_Name}_POPULATED)
  FetchContent_Populate(FetchContent_libb)
  message(STATUS "FetchContent_libb source dir: ${${lc_libb_Name}_SOURCE_DIR}")
  message(STATUS "FetchContent_libb binary dir: ${${lc_libb_Name}_BINARY_DIR}")
  add_subdirectory(${${lc_libb_Name}_SOURCE_DIR} ${${lc_libb_Name}_BINARY_DIR})
endif()

include_directories(${${lc_libb_Name}_SOURCE_DIR})

add_library(fc_lib_a STATIC fc_lib_a.c)

add_executable(test test.c)
target_link_libraries(test fc_lib_a fc_lib_b)
