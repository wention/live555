# CMakeLists.txt testProgs directory

# headers
set(COMMON_HDRS
    playCommon.hh
    )

set(COMMON_SRCS
    playCommon.cpp
    )

# source files for MediaPreEncoderServer
set(OPEN_RTSP_SRCS
    ${COMMON_SRCS}
    openRTSP.cpp
    )

set(PLAY_SIP_SRCS
    ${COMMON_SRCS}
    playSIP.cpp
    )

set(TEST_AMR_AUDIO_STREAMER_SRCS
    ${COMMON_SRCS}
    testAMRAudioStreamer.cpp
    )

set(TEST_H264_VIDEO_STREAMER_SRCS
    ${COMMON_SRCS}
    testH264VideoStreamer.cpp
    )

set(TEST_H264_VIDEO_TO_HLS_SEGMENTS_SRCS
    testH264VideoToHLSSegments.cpp
    )

set(TEST_H265_VIDEO_STREAMER_SRCS
    ${COMMON_SRCS}
    testH265VideoStreamer.cpp
    )

set(ON_DEMAND_RTSP_SERVER_SRCS
    ${COMMON_SRCS}
    testOnDemandRTSPServer.cpp
    )

set(TEST_RTSP_CLIENT_SRCS 
    testRTSPClient.cpp
    )

set(TEST_XXX_LIBS
    BasicUsageEnvironment
    groupsock
    liveMedia
    UsageEnvironment
    )

if (WIN32)
    set(TEST_XXX_LIBS ${TEST_XXX_LIBS} ws2_32 winmm)
endif()

add_executable(openRTSP ${COMMON_HDRS} ${OPEN_RTSP_SRCS})
target_link_libraries(
    openRTSP
    ${TEST_XXX_LIBS}
    )

add_executable(playSIP ${COMMON_HDRS} ${PLAY_SIP_SRCS})
target_link_libraries(
    playSIP
    ${TEST_XXX_LIBS}
    )

add_executable(testAmrAudioStreamer ${COMMON_HDRS} ${TEST_AMR_AUDIO_STREAMER_SRCS})
target_link_libraries(
    testAmrAudioStreamer
    ${TEST_XXX_LIBS}
    )

add_executable(testH264VideoStreamer ${COMMON_HDRS} ${TEST_H264_VIDEO_STREAMER_SRCS})
target_link_libraries(
    testH264VideoStreamer
    ${TEST_XXX_LIBS}
    )

add_executable(testH264VideotoHLSSegments ${COMMON_HDRS} ${TEST_H264_VIDEO_TO_HLS_SEGMENTS_SRCS})
target_link_libraries(
    testH264VideotoHLSSegments
    ${TEST_XXX_LIBS}
    hlsProxy
)

add_executable(testH265VideoStreamer ${COMMON_HDRS} ${TEST_H265_VIDEO_STREAMER_SRCS})
target_link_libraries(
    testH265VideoStreamer
    ${TEST_XXX_LIBS}
    )

add_executable(testOnDemandRTSPServer ${COMMON_HDRS} ${ON_DEMAND_RTSP_SERVER_SRCS})
target_link_libraries(
    testOnDemandRTSPServer
    ${TEST_XXX_LIBS}
    )

add_executable(testRTSPClient ${COMMON_HDRS} ${TEST_RTSP_CLIENT_SRCS})
target_link_libraries(
    testRTSPClient
    ${TEST_XXX_LIBS}
    )
