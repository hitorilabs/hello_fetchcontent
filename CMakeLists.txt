cmake_minimum_required(VERSION 3.10)
project(hello-fetchcontent VERSION 1.0)

add_library(hello-fetchcontent src/hello.cpp)
target_include_directories(hello-fetchcontent PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")

install(TARGETS hello-fetchcontent
        EXPORT src/hello.cpp
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin)
install(DIRECTORY include/ DESTINATION include)

