cmake_minimum_required(VERSION 3.11)
project(hello_fetchcontent VERSION 1.0)

add_library(hello_fetchcontent src/hello.cpp)
add_library(hello_fetchcontent::hello_fetchcontent ALIAS hello_fetchcontent)

target_include_directories(hello_fetchcontent INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}/include")

install(TARGETS hello_fetchcontent
        EXPORT src/hello.cpp
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin)

install(DIRECTORY include/ DESTINATION include)

install(EXPORT src/hello.cpp
        FILE hello_fetchcontent.cmake
        NAMESPACE hello_fetchcontent::
        DESTINATION lib/cmake/hello_fetchcontent)

