cmake_minimum_required(VERSION 3.8)
project(tunsocks)

set(CMAKE_C_STANDARD 99)

include_directories(lwip/src/include)
include_directories(lwip/src/include/ipv4)
include_directories(lwip/src/include/ipv6)
include_directories(include)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -O2 -g")

set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH}" "${CMAKE_CURRENT_SOURCE_DIR}/build/cmake")

include(build/cmake/FindLibevent.cmake)
include(build/cmake/FindPCAP.cmake)

set(SOURCE_FILES
        lwip/src/api/err.c
        lwip/src/core/init.c
        lwip/src/core/def.c
        lwip/src/core/mem.c
        lwip/src/core/memp.c
        lwip/src/core/netif.c
        lwip/src/core/pbuf.c
        lwip/src/core/stats.c
        lwip/src/core/dns.c
        lwip/src/core/udp.c
        lwip/src/core/sys.c
        lwip/src/core/raw.c
        lwip/src/core/tcp.c
        lwip/src/core/tcp_in.c
        lwip/src/core/tcp_out.c
        lwip/src/core/inet_chksum.c
        lwip/src/core/ipv4/icmp.c
        lwip/src/core/ipv4/ip4.c
        lwip/src/core/ipv4/ip4_addr.c
        lwip/src/core/ipv4/ip_frag.c
        lwip/src/core/ipv6/nd6.c
        lwip/src/core/ipv6/mld6.c
        lwip/src/core/ipv6/icmp6.c
        lwip/src/core/ipv6/ip6.c
        lwip/src/core/ipv6/ip6_addr.c
        lwip/src/core/ipv6/ip6_frag.c
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
