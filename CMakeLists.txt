cmake_minimum_required(VERSION 3.11)

project (FetchContent_top)

include(FetchContent)

FetchContent_Declare(FetchContent_liba
    GIT_REPOSITORY https://github.com/cmaketest/FetchContent_liba.git
)

FetchContent_GetProperties(FetchContent_liba)
string(TOLOWER "FetchContent_liba" lc_liba_Name)
if(NOT ${lc_liba_Name}_POPULATED)
  FetchContent_Populate(FetchContent_liba)
  message(STATUS "FetchContent_liba source dir: ${${lc_liba_Name}_SOURCE_DIR}")
  message(STATUS "FetchContent_liba binary dir: ${${lc_liba_Name}_BINARY_DIR}")
  add_subdirectory(${${lc_liba_Name}_SOURCE_DIR} ${${lc_liba_Name}_BINARY_DIR})
endif()

include_directories(${${lc_liba_Name}_SOURCE_DIR})


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


add_executable(top main.c)
target_link_libraries(top fc_lib_a fc_lib_b)
