
set(HLSPROXY_SRCS
    live555HLSProxy.cpp
    )

add_library(hlsProxy STATIC ${HLSPROXY_SRCS})
target_include_directories(hlsProxy PUBLIC ${OPENSSL_INCLUDE_DIR})
target_link_libraries(hlsProxy PUBLIC
    ${OPENSSL_LIBRARIES}
    )
