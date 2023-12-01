cmake_minimum_required(VERSION 3.22)
project(yet-another-userver-demo LANGUAGES CXX)

set(BUILD_SHARED_LIBS OFF)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_EXTENSIONS OFF)

message(STATUS "Using toolchain file: ${CMAKE_TOOLCHAIN_FILE}")

include(third_party/userver/cmake/SetupEnvironment.cmake)
include(GNUInstallDirs)
add_subdirectory(third_party/userver)

include(GrpcTargets)
add_grpc_library(yet-another-userver-demo-proto PROTOS samples/greeter.proto)

add_executable(${PROJECT_NAME}
    src/components/samples/greeter_service_component.cpp
    src/components/samples/greeter_service_component.h
    src/main.cpp
)
target_link_libraries(${PROJECT_NAME}
    PRIVATE
        yet-another-userver-demo-proto
)
target_compile_options(${PROJECT_NAME}
    PRIVATE
        -Werror
        -Wall
        -Wextra
        -Wassign-enum
        -Wcast-align
        -Wcast-qual
        -Wconversion
        -Wextra-semi
        -Wsign-compare
        -Wsign-conversion
        -pedantic
        -pedantic-errors
)
