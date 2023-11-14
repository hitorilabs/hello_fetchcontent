cmake_minimum_required(VERSION 3.14)
project(hello_fetchcontent VERSION 1.0)

add_library(hello SHARED src/hello.cpp)
add_library(hello_fetchcontent::hello ALIAS hello)

target_include_directories(hello PUBLIC 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>)



install(TARGETS hello
        EXPORT helloTargets
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib)

install(DIRECTORY include/ DESTINATION include)

install(EXPORT helloTargets
        FILE helloTargets.cmake
        NAMESPACE hello_fetchcontent::
        DESTINATION lib/cmake/hello_fetchcontent)

