
set(HLSPROXY_SRCS
    live555HLSProxy.cpp
    )

set(HLSPROXY_SRCS
    live555HLSProxy.cpp
    )

add_executable(hlsProxy ${HLSPROXY_SRCS})
target_link_libraries(hlsProxy PUBLIC
    BasicUsageEnvironment
    groupsock
    liveMedia
    UsageEnvironment
    ${LINK_LIBS}
    )

if (OPENSSL_FOUND)
    target_include_directories(hlsProxy PUBLIC ${OPENSSL_INCLUDE_DIR})
    target_link_libraries(hlsProxy PUBLIC
        ${OPENSSL_LIBRARIES}
    )
endif()
