cmake_minimum_required(VERSION 3.16)

set(CMAKE_CXX_STANDARD 17)

project(voip_gw_test)
set(TEST_PROJECT_NAME
    ${PROJECT_NAME}
    )

find_package(PkgConfig REQUIRED)
pkg_search_module(VOIPGW REQUIRED voipgw)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC -W -Wall -Wno-unused-parameter -Werror=return-type -Werror=reorder -Wno-switch -Wno-deprecated-declarations")

include_directories(
    ${PROJECT_SOURCE_DIR}
    ${VOIPGW_INCLUDE_DIRS}
    )
    
link_directories(
    ${VOIPGW_LIBRARY_DIRS}
    )

set(SOURCES
    api_test.cpp
    c_api_test.c
    main.cpp
)

set(PUBLIC_HEADERS
)

set(PRIVATE_HEADERS
    c_api_test.h
    api_test.h
)

add_executable(${PROJECT_NAME}
    ${SOURCES}
    ${PUBLIC_HEADERS}
    ${PRIVATE_HEADERS}
)

target_link_libraries(${TEST_PROJECT_NAME}
    ${VOIPGW_LIBRARIES}
    )


    




