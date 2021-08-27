# CMAKE VERSION
cmake_minimum_required(VERSION 3.18.0)

include(cmake/udph.cmake)

PROJECT_CREATE(libudph)

PROJECT_LOAD_GIT_SUBMODULE(libudph_Class "https://github.com/udPhish/libudph_Class.git" master)
PROVIDE_PROJECT(libudph_Class)
PROJECT_LOAD_GIT_SUBMODULE(libudph_Container "https://github.com/udPhish/libudph_Container.git" master)
PROVIDE_PROJECT(libudph_Container)
PROJECT_LOAD_GIT_SUBMODULE(libudph_Math "https://github.com/udPhish/libudph_Math.git" as_static_lib)
PROVIDE_PROJECT(libudph_Math)

TARGET_CREATE_LIB(libudph INTERFACE)

TARGET_APPEND_DEP_INTERFACE(libudph libudph::Class)
TARGET_APPEND_DEP_INTERFACE(libudph libudph::Container)
TARGET_APPEND_DEP_INTERFACE(libudph libudph::Math)

TARGET_LINK(libudph)

TARGET_PACKAGE(libudph)

FINALIZE()