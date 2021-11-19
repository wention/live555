# CMakeLists.txt in liveMedia

file(GLOB_RECURSE LIVE_MEDIA_SRCS
    *c
    *.cpp
    )

file(GLOB_RECURSE LIVE_MEDIA_HEADERS
    include/*.hh
    )

add_library(liveMedia STATIC ${LIVE_MEDIA_HEADERS} ${LIVE_MEDIA_SRCS})
target_include_directories(liveMedia PUBLIC ${OPENSSL_INCLUDE_DIR})
target_link_libraries(liveMedia PUBLIC
    ${OPENSSL_LIBRARIES}
    )
