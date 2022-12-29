project(rtspclisvr)

set(LIBRARY_NAME rtspclisvr)

# check CMake version
cmake_minimum_required(VERSION 3.13 FATAL_ERROR)

file(GLOB SRC_LIST "src/Common/*.cpp" "src/OS_Common/*.cpp" "src/Util/*.cpp" "src/Util/*.c" "src/Sock/*.cpp" "src/RTSPClient/*/*.cpp" "src/RTSPClient/*/*.c" "src/RTSPServer/*/*.cpp" "src/RTSPServer/*/*.c")

add_library(${LIBRARY_NAME} STATIC
    ${SRC_LIST}
)

add_definitions(-DLINUX)
add_definitions(-fPIC)

target_include_directories(${LIBRARY_NAME} PRIVATE include)

install(TARGETS ${LIBRARY_NAME} DESTINATION lib)
file(GLOB HEADER  include/*)
install(FILES ${HEADER} DESTINATION include/rtspclisvr)
