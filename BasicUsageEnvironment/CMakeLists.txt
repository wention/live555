# CMakeLists.txt in BasicUsageEnvironment

set(BASIC_USAGE_ENVIRONMENT_SRCS
    BasicHashTable.cpp
    BasicTaskScheduler.cpp
    BasicTaskScheduler0.cpp
    BasicUsageEnvironment.cpp
    BasicUsageEnvironment0.cpp
    DelayQueue.cpp
    )

set(BASIC_USAGE_ENVIRONMENT_HEADERS
    include/BasicHashTable.hh
    include/BasicUsageEnvironment.hh
    include/BasicUsageEnvironment0.hh
    include/BasicUsageEnvironment_version.hh
    include/DelayQueue.hh
    include/HandlerSet.hh
    )

add_library(BasicUsageEnvironment ${BASIC_USAGE_ENVIRONMENT_HEADERS} ${BASIC_USAGE_ENVIRONMENT_SRCS})
