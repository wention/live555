# CMakeLists.txt testProgs directory

set(PLAY_COMMON_SRCS
    playCommon.hh
    playCommon.cpp
)

set(HELPER_SRCS
    announceURL.hh
    announceURL.cpp
)

# source files for MediaPreEncoderServer
set(OPEN_RTSP_SRCS
    ${PLAY_COMMON_SRCS}
    openRTSP.cpp
)

set(PLAY_SIP_SRCS
    ${PLAY_COMMON_SRCS}
    playSIP.cpp
    )

set(TEST_AMR_AUDIO_STREAMER_SRCS
    ${HELPER_SRCS}
    testAMRAudioStreamer.cpp
    )

set(TEST_H264_VIDEO_STREAMER_SRCS
    ${HELPER_SRCS}
    testH264VideoStreamer.cpp
    )

set(TEST_H264_VIDEO_TO_HLS_SEGMENTS_SRCS
    ${HELPER_SRCS}
    testH264VideoToHLSSegments.cpp
    )

set(TEST_H265_VIDEO_STREAMER_SRCS
    ${HELPER_SRCS}
    testH265VideoStreamer.cpp
    )

set(TEST_ON_DEMAND_RTSP_SERVER_SRCS
    ${HELPER_SRCS}
    testOnDemandRTSPServer.cpp
    )

set(TEST_RTSP_CLIENT_SRCS 
    testRTSPClient.cpp
    )

set(TEST_XXX_LIBS
    liveMedia
    groupsock
    BasicUsageEnvironment
    UsageEnvironment
    ${LINK_LIBS}
    )

if (WIN32)
    set(TEST_XXX_LIBS ${TEST_XXX_LIBS} ws2_32 winmm)
endif()

add_executable(openRTSP ${OPEN_RTSP_SRCS})
target_link_libraries(
    openRTSP
    ${TEST_XXX_LIBS}
    )

add_executable(playSIP ${PLAY_SIP_SRCS})
target_link_libraries(
    playSIP
    ${TEST_XXX_LIBS}
    )

add_executable(testAmrAudioStreamer ${TEST_AMR_AUDIO_STREAMER_SRCS})
target_link_libraries(
    testAmrAudioStreamer
    ${TEST_XXX_LIBS}
    )

add_executable(testH264VideoStreamer ${TEST_H264_VIDEO_STREAMER_SRCS})
target_link_libraries(
    testH264VideoStreamer
    ${TEST_XXX_LIBS}
    )

add_executable(testH264VideotoHLSSegments ${TEST_H264_VIDEO_TO_HLS_SEGMENTS_SRCS})
target_link_libraries(
    testH264VideotoHLSSegments
    ${TEST_XXX_LIBS}
)

add_executable(testH265VideoStreamer ${TEST_H265_VIDEO_STREAMER_SRCS})
target_link_libraries(
    testH265VideoStreamer
    ${TEST_XXX_LIBS}
    )

add_executable(testOnDemandRTSPServer ${TEST_ON_DEMAND_RTSP_SERVER_SRCS})
target_link_libraries(
    testOnDemandRTSPServer
    ${TEST_XXX_LIBS}
    )

add_executable(testRTSPClient ${TEST_RTSP_CLIENT_SRCS})
target_link_libraries(
    testRTSPClient
    ${TEST_XXX_LIBS}
    )
