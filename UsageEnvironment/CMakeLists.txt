# CMakeLists.txt in UsageEnvironment

set(USAGE_ENVIRONMENT_SRCS
    HashTable.cpp
    strDup.cpp
    UsageEnvironment.cpp
    )

set(USAGE_ENVIRONMENT_HEADERS
    include/Boolean.hh
    include/HashTable.hh
    include/strDup.hh
    include/UsageEnvironment.hh
    include/UsageEnvironment_version.hh
    )

include_directories(
    ${live555Includes}
    )

add_library(UsageEnvironment STATIC ${USAGE_ENVIRONMENT_HEADERS} ${USAGE_ENVIRONMENT_SRCS})
