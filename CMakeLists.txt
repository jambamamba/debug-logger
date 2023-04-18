cmake_minimum_required (VERSION 3.8)
set (project "debug_logger")
project(${project} CXX C)

# make cache variables for install destinations
include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(SOURCES
   debug_logger.h
   debug_logger.c
   file_utils.h
   file_utils.cpp
)

#todo:
set (INC_DIRS
    ${PROJECT_SOURCE_DIR}/
    )

set(LIBS
)
add_library (${project} SHARED ${SOURCES})
target_include_directories(${project} PUBLIC ${INC_DIRS})
target_link_directories(${project} PRIVATE ${LINK_DIRECTORIES})
target_link_libraries(${project} PUBLIC ${LIBS})

if(MINGW)
    add_compile_definitions(MINGW)
endif()

