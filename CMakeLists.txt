cmake_minimum_required(VERSION 2.6)

PROJECT( live555 )

SET(EXECUTABLE_OUTPUT_PATH ${live555_SOURCE_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${live555_SOURCE_DIR}/lib)
SET(RUNTIME_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)

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
INCLUDE_DIRECTORIES(
${live555Includes}
)

ADD_SUBDIRECTORY(BasicUsageEnvironment)
ADD_SUBDIRECTORY(groupsock)
ADD_SUBDIRECTORY(liveMedia)
ADD_SUBDIRECTORY(mediaServer)
ADD_SUBDIRECTORY(proxyServer)
ADD_SUBDIRECTORY(UsageEnvironment)
ADD_SUBDIRECTORY(testProgs)
