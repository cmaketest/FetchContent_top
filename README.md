FetchContent_top

This repo demonstrates cmake's FetchContent feature.

There are 3 libraries in play here:
top - depends upon liba and libb
liba - depends upon libb
libb - no dependencies

The goal here is to build 'top', liba, and only one copy of libb!
