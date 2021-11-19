# CMakeLists.txt proxyServer directory

# source files for proxyServer
set(PROXY_SERVER_SRCS 
    live555ProxyServer.cpp
    )

set(PROXY_SERVER_LIBS
    BasicUsageEnvironment
    groupsock
    liveMedia
    UsageEnvironment
    )

if (WIN32)
    set(PROXY_SERVER_LIBS ${PROXY_SERVER_LIBS} ws2_32 winmm)
endif()

add_executable(proxyServer ${PROXY_SERVER_SRCS})

target_link_libraries(
    proxyServer
    ${PROXY_SERVER_LIBS}
    ) 

