cmake_minimum_required(VERSION 3.8)
project(tunsocks)

set(CMAKE_C_STANDARD 99)

set(LWIP_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lwip)
include(lwip/src/Filelists.cmake)

include_directories(lwip/src/include)
include_directories(lwip/src/include/ipv4)
include_directories(lwip/src/include/ipv6)
include_directories(include)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -O2 -g")

set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH}" "${CMAKE_CURRENT_SOURCE_DIR}/build/cmake")

include_directories(../libevent/include)

include(build/cmake/FindLibevent.cmake)
include(build/cmake/FindPCAP.cmake)

set(SOURCE_FILES
        src/libevent.c
        src/socks5.c
        src/socks.c
        src/forward_local.c
        src/forward_remote.c
        src/tunif.c
        src/pipe.c
        src/host.c
        src/main.c)

add_executable(tunsocks ${SOURCE_FILES})
