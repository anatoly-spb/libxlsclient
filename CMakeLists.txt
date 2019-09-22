cmake_minimum_required(VERSION 3.12)

project(xlstestroot)

add_subdirectory(thirdparty)

find_package(xls REQUIRED)

add_subdirectory(src)

