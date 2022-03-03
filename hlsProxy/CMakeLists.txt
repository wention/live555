
set(HLSPROXY_SRCS
    live555HLSProxy.cpp
    )

set(HLSPROXY_SRCS
    live555HLSProxy.cpp
    )

add_executable(hlsProxy ${HLSPROXY_SRCS})
target_include_directories(hlsProxy PUBLIC ${OPENSSL_INCLUDE_DIR})
target_link_libraries(hlsProxy PUBLIC
    BasicUsageEnvironment
    groupsock
    liveMedia
    UsageEnvironment
    ${OPENSSL_LIBRARIES}
    )
