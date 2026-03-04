cmake_minimum_required(VERSION 3.16)
project(app CXX)

set(CMAKE_CXX_STANDARD 20)
#src dir is where the code files are
file(GLOB SRC_FILES "./*.cpp")

add_executable(app ${SRC_FILES})

if(EXISTS "${CMAKE_SOURCE_DIR}/include")
    target_include_directories(app PRIVATE include)
else()
    target_include_directories(app PRIVATE src)
endif()

if(EXISTS "${CMAKE_SOURCE_DIR}/lib")
    target_link_directories(app PRIVATE lib)
endif()