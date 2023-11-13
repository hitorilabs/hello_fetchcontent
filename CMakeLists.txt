cmake_minimum_required(VERSION 3.10)
project(hello_fetchcontent VERSION 1.0)

add_library(hello_fetchcontent src/hello.cpp)
add_library(MyLibrary::MyLibrary ALIAS MyLibrary)

target_include_directories(hello_fetchcontent PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")

install(TARGETS hello_fetchcontent
        EXPORT src/hello.cpp
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin)

install(DIRECTORY include/ DESTINATION include)

install(EXPORT src/hello.cpp
        FILE hello.cmake
        NAMESPACE hello_fetchcontent::
        DESTINATION lib/cmake/hello_fetchcontent)

