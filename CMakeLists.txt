cmake_minimum_required(VERSION 3.10)

project( live555 )

#set(EXECUTABLE_OUTPUT_PATH ${live555_SOURCE_DIR}/bin)
#set(LIBRARY_OUTPUT_PATH ${live555_SOURCE_DIR}/lib)
#set(RUNTIME_OUTPUT_DIRECTORY ${live555_SOURCE_DIR}/bin)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

option(WITH_OPENSSL "with openssl")


if (${WITH_OPENSSL})
    find_package(OpenSSL REQUIRED)
else()
    find_package(OpenSSL)
endif()


if (NOT OpenSSL_FOUND)
    add_definitions(-DNO_OPENSSL=1)
endif()

if (MSVC OR MINGW)
    set(CMAKE_STATIC_LIBRARY_SUFFIX ".lib.a")
endif()


include(CheckSymbolExists)
check_symbol_exists(getifaddrs "ifaddrs.h" HAVE_GETIFADDRS)

if(NOT HAVE_GETIFADDRS)
    add_definitions(-DNO_GETIFADDRS)
endif()

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

set(LINK_LIBS)

if (MSVC OR MINGW)
 set(LINK_LIBS Ws2_32 winmm)
endif()

add_subdirectory(BasicUsageEnvironment)
add_subdirectory(groupsock)
add_subdirectory(liveMedia)
add_subdirectory(hlsProxy)
add_subdirectory(mediaServer)
add_subdirectory(proxyServer)
add_subdirectory(UsageEnvironment)
add_subdirectory(testProgs)

if (MSVC OR MINGW)
    add_subdirectory(WindowsAudioInputDevice)
endif()
