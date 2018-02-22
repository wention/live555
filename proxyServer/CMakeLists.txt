# CMakeLists.txt proxyServer directory

# source files for proxyServer
SET(PROXY_SERVER_SRCS 
live555ProxyServer.cpp
)

SET(PROXY_SERVER_LIBS
BasicUsageEnvironment
groupsock
liveMedia
UsageEnvironment
)

if (WIN32)
    SET(PROXY_SERVER_LIBS ${PROXY_SERVER_LIBS} ws2_32 winmm)
endif()

ADD_EXECUTABLE(proxyServer ${PROXY_SERVER_SRCS})

TARGET_LINK_LIBRARIES(
proxyServer
${PROXY_SERVER_LIBS}
) 

