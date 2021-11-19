cmake_minimum_required(VERSION 2.8.12)

project( live555 )

#set(EXECUTABLE_OUTPUT_PATH ${live555_SOURCE_DIR}/bin)
#set(LIBRARY_OUTPUT_PATH ${live555_SOURCE_DIR}/lib)
#set(RUNTIME_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)

find_package(OpenSSL REQUIRED)

# includes
SET(live555Includes
    ${live555_SOURCE_DIR}/BasicUsageEnvironment/include
    ${live555_SOURCE_DIR}/groupsock/include
    ${live555_SOURCE_DIR}/liveMedia/include
    ${live555_SOURCE_DIR}/UsageEnvironment/include
    )

if (APPLE)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DBSD=1 -O -DSOCKLEN_T=socklen_t -DHAVE_SOCKADDR_LEN=1 -DTIME_BASE=int -DNEED_XLOCALE_H=1")
endif()

# includes
include_directories(
    ${live555Includes}
    )

add_subdirectory(BasicUsageEnvironment)
add_subdirectory(groupsock)
add_subdirectory(liveMedia)
add_subdirectory(hlsProxy)
add_subdirectory(mediaServer)
add_subdirectory(proxyServer)
add_subdirectory(UsageEnvironment)
add_subdirectory(testProgs)
