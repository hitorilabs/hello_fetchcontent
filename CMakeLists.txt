# cmake_minimum_required(VERSION 3.11)
# project(hello_fetchcontent VERSION 1.0)
# 
# add_library(hello_fetchcontent src/hello.cpp)
# add_library(hello_fetchcontent::hello_fetchcontent ALIAS hello_fetchcontent)
# 
# target_include_directories(hello_fetchcontent PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
# 
# install(TARGETS hello_fetchcontent
#         EXPORT HelloFetchContentTargets
#         LIBRARY DESTINATION lib
#         ARCHIVE DESTINATION lib
#         RUNTIME DESTINATION bin)
# 
# install(DIRECTORY include/ DESTINATION include)
# 
# install(EXPORT HelloFetchContentTargets
#         FILE HelloFetchContentTargets.cmake
#         NAMESPACE hello_fetchcontent::
#         DESTINATION lib/cmake/hello_fetchcontent)

cmake_minimum_required(VERSION 3.14)
project(hello_fetchcontent VERSION 1.0)

add_library(hello src/hello.cpp)

# target_include_directories(hello PUBLIC include)
# Specify include directories for when building the library
target_include_directories(hello PUBLIC 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)


add_library(hello_fetchcontent::hello ALIAS hello)

install(TARGETS hello
        EXPORT helloTargets
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib)

install(DIRECTORY include/ DESTINATION include)

install(EXPORT helloTargets
        FILE helloTargets.cmake
        NAMESPACE hello_fetchcontent::
        DESTINATION lib/cmake/hello_fetchcontent)

