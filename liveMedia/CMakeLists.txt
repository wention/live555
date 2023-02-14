# CMakeLists.txt in liveMedia

file(GLOB_RECURSE LIVE_MEDIA_SRCS
    *c
    *.cpp
    )

file(GLOB_RECURSE LIVE_MEDIA_HEADERS
    include/*.hh
    )

add_library(liveMedia
    ${LIVE_MEDIA_HEADERS}
    ${LIVE_MEDIA_SRCS}
)

if (OPENSSL_FOUND)
    target_include_directories(liveMedia PRIVATE
        ${OPENSSL_INCLUDE_DIR}
    )
    target_link_libraries(liveMedia PRIVATE
        ${OPENSSL_LIBRARIES}
    )
endif()
