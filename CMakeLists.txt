# CMAKE VERSION
cmake_minimum_required(VERSION 3.18.0)

include(cmake/udph.cmake)

project(libudph VERSION "${GIT_VERSION}" LANGUAGES CXX)

include(udphInit)

TARGET_CREATE_LIB(libudph INTERFACE)

TARGET_APPEND_DEP(libudph libudph::Math)
TARGET_APPEND_DEP(libudph libudph::Class)

TARGET_LINK(libudph)

TARGET_PACKAGE(libudph)

include(udphFinalize)