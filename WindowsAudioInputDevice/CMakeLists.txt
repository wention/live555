include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}
)

set(LOCAL_LIBS
    liveMedia
    groupsock
    BasicUsageEnvironment
    UsageEnvironment
    ${LINK_LIBS}
)

add_library(WindowsAudioInputPorts_noMixer
    WindowsAudioInputDevice_common.hh
    WindowsAudioInputDevice_common.cpp
    WindowsAudioInputDevice_noMixer.hh
    WindowsAudioInputDevice_noMixer.cpp
)


add_library(WindowsAudioInputPorts_mixer
    WindowsAudioInputDevice_common.hh
    WindowsAudioInputDevice_common.cpp
    WindowsAudioInputDevice_mixer.hh
    WindowsAudioInputDevice_mixer.cpp
)

add_executable(showAudioInputPorts_noMixer
    showAudioInputPorts.cpp
)

target_link_libraries(showAudioInputPorts_noMixer
    WindowsAudioInputPorts_noMixer
    ${LOCAL_LIBS}
)

add_executable(showAudioInputPorts_mixer
    showAudioInputPorts.cpp
)

target_link_libraries(showAudioInputPorts_mixer
    WindowsAudioInputPorts_noMixer
    ${LOCAL_LIBS}
)