FetchContent_top

This repo demonstrates cmake's FetchContent feature.

There are 3 repos in play here:
* top - (executable) depends upon liba and libb
* liba - depends upon libb
* libb - no dependencies

The goal here is to build 'top', liba, and only one copy of libb!


To build:
1. mkdir build
2. cd build
3. cmake ..
4. make

