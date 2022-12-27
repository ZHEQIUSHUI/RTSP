project(rtspclisvr)

# check CMake version
cmake_minimum_required(VERSION 3.13 FATAL_ERROR)

file(GLOB SRC_LIST "src/Common/*.cpp" "src/OS_Common/*.cpp" "src/Util/*.cpp" "src/Util/*.c" "src/Sock/*.cpp" "src/RTSPClient/*/*.cpp" "src/RTSPServer/*/*.cpp")

add_library(${CMAKE_PROJECT_NAME} STATIC
    ${SRC_LIST}
)

add_definitions(-DLINUX)

target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/Common)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/OS_Common)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/Util)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/Sock)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/RTSPClient/Common)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/RTSPClient/RTP)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/RTSPClient/RTSP)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/RTSPClient/RTCP)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/RTSPServer/RTSP)
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE src/RTSPServer/Common)

install(TARGETS ${CMAKE_PROJECT_NAME} DESTINATION lib)
file(GLOB HEADER "src/Common/*.h" "src/OS_Common/*.h" "src/Util/*.h" "src/Sock/*.h" "src/RTSPClient/*/*.h" "src/RTSPServer/*/*.h"
                                        "src/Common/*.hh" "src/OS_Common/*.hh" "src/Util/*.hh" "src/Sock/*.hh" "src/RTSPClient/*/*.hh" "src/RTSPServer/*/*.hh")
install(FILES ${HEADER} DESTINATION include)