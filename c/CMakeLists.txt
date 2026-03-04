cmake_minimum_required(VERSION 3.16)
project(app C)

set(CMAKE_C_STANDARD 17)

file(GLOB SRC_FILES "src/*.c")

add_executable(app ${SRC_FILES})

if(EXISTS "${CMAKE_SOURCE_DIR}/include")
    target_include_directories(app PRIVATE include)
else()
    target_include_directories(app PRIVATE src)
endif()

if(EXISTS "${CMAKE_SOURCE_DIR}/lib")
    target_link_directories(app PRIVATE lib)
endif()