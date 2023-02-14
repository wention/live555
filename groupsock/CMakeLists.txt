# CMakeLists.txt in groupsock

set(GROUPSOCK_SRCS
    GroupEId.cpp
    Groupsock.cpp
    GroupsockHelper.cpp
    inet.c
    IOHandlers.cpp
    NetAddress.cpp
    NetInterface.cpp
)

set(GROUPSOCK_HEADERS
    include/GroupEId.hh
    include/Groupsock.hh
    include/groupsock_version.hh
    include/GroupsockHelper.hh
    include/IOHandlers.hh
    include/NetAddress.hh
    include/NetInterface.hh
    include/NetCommon.h
)

add_library(groupsock
    ${GROUPSOCK_HEADERS}
    ${GROUPSOCK_SRCS}
)
