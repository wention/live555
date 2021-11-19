
# CMakeLists.txt mediaServer directory

# headers
set(MEDIA_SERVER_HDRS
    DynamicRTSPServer.hh
    )

# source files for mediaServer
set(MEDIA_SERVER_SRCS 
    DynamicRTSPServer.cpp
    live555MediaServer.cpp
    )

set(MEDIA_SERVER_LIBS
    BasicUsageEnvironment
    groupsock
    liveMedia
    UsageEnvironment
    )

if (WIN32)
    set(MEDIA_SERVER_LIBS ${MEDIA_SERVER_LIBS} ws2_32 winmm)
endif()

add_executable(mediaServer ${MEDIA_SERVER_HDRS} ${MEDIA_SERVER_SRCS})

target_link_libraries(
    mediaServer
    ${MEDIA_SERVER_LIBS}
    ) 
