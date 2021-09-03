cmake_minimum_required(VERSION 3.0)

project(jsimn)

message("Platform:  ${CMAKE_SYSTEM_NAME}")
if (${CMAKE_SYSTEM_NAME} MATCHES "Windows")
    set(WINDOWS TRUE)
    set(PLATFORM "win")
elseif (${CMAKE_SYSTEM_NAME} MATCHES "Linux")
    set(LINUX TRUE)
    set(PLATFORM "linux")
elseif (${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
    set(MACOSX TRUE)
    set(PLATFORM "mac")
endif()

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_subdirectory(device)
add_subdirectory(jsimtxt)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin/${PLATFORM}/${CMAKE_BUILD_TYPE})

add_executable(jsim_n ${JSIM_DEV} ${JSIM_TXT} main_n.c)

target_link_libraries(jsim_n m)
