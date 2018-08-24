include_directories(${SHSDK_INCLUDE_DIRS} "../Plugins")

set(SOURCES_GAME Game.cpp Game.h)
source_group("" FILES ${SOURCES_GAME})

if (MSVC)
    SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /FORCE:MULTIPLE")
endif (MSVC)

# Compile Project
set(TARGET_NAME "${PROJECT_NAME}")

# All other platforms use Executables
add_executable(${TARGET_NAME} WIN32 ${SOURCES_GAME})

set_property(TARGET ${TARGET_NAME} APPEND PROPERTY COMPILE_DEFINITIONS "${SHSDK_COMPILE_DEFINITIONS}")
set_property(TARGET ${TARGET_NAME} APPEND PROPERTY COMPILE_FLAGS "${SHSDK_COMPILE_FLAGS}")
set_property(TARGET ${TARGET_NAME} APPEND PROPERTY COMPILE_DEFINITIONS "SH_$<UPPER_CASE:$<CONFIG>>=1")

target_link_libraries(${TARGET_NAME} Plugin) # link with plugins
target_link_libraries(${TARGET_NAME} ${SHSDK_LIBRARIES})

CopyToShineSAAS(${TARGET_NAME})
