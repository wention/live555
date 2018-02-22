
# CMakeLists.txt mediaServer directory

# headers
SET(MEDIA_SERVER_HDRS
DynamicRTSPServer.hh
)

# source files for mediaServer
SET(MEDIA_SERVER_SRCS 
DynamicRTSPServer.cpp
live555MediaServer.cpp
)

SET(MEDIA_SERVER_LIBS
BasicUsageEnvironment
groupsock
liveMedia
UsageEnvironment
)

if (WIN32)
    SET(MEDIA_SERVER_LIBS ${MEDIA_SERVER_LIBS} ws2_32 winmm)
endif()

ADD_EXECUTABLE(mediaServer ${MEDIA_SERVER_HDRS} ${MEDIA_SERVER_SRCS})

TARGET_LINK_LIBRARIES(
mediaServer
${MEDIA_SERVER_LIBS}
) 
