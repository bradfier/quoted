cmake_minimum_required(VERSION 3.1)
project (quoted)
set (CMAKE_CXX_STANDARD 11)

add_subdirectory(crow)
include_directories(crow/include)

find_package(Boost COMPONENTS system REQUIRED)
if(Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
    add_executable(main src/main.cpp)
    target_link_libraries(main ${Boost_SYSTEM_LIBRARY})
endif()

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(main Threads::Threads)
