cmake_minimum_required(VERSION 3.10)
project(lua VERSION 5.4.6)

option(LUA_BUILD_SHARED      "Build lua shared library"      ON)
option(LUA_BUILD_STATIC      "Build lua static library"      ON)
option(LUA_BUILD_LUA         "Build lua executable"          ON)
option(LUA_BUILD_LUAC        "Build lua compiler"            ON)
option(LUA_ENABLE_TEST       "Enable lua test"               ON)

add_subdirectory(src)

if(${LUA_ENABLE_TEST})

    if(NOT ${LUA_BUILD_LUA})
        message(WARNING "lua executable is not built, skip test")
    else()
        enable_testing()
        add_test(
            NAME lua-testsuite
            COMMAND $<TARGET_FILE:lua> -e "_U=true" all.lua
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/tests
        )
    endif()
endif()
