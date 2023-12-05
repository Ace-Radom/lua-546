cmake_minimum_required(VERSION 3.10)
project(lua VERSION 5.4.6)

option(LUA_BUILD_SHARED_ONLY "Only build lua shared library" OFF)

add_subdirectory(src)
