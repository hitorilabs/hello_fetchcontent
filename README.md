# cmake-fetchcontent-example
example of a repo that's ready to use with `FetchContent_Declare`

This is the most basic project structure for a project that can be pulled in using `FetchContent_Declare`:

```
MyLibrary/
│
├── include/
│   └── MyLibrary/
│       └── hello.h
│
└── src/
    └── hello.cpp
└── CMakeLists.txt
```

> Include directories usage requirements commonly differ between the build-tree and the install-tree. The BUILD_INTERFACE and INSTALL_INTERFACE generator expressions can be used to describe separate usage requirements based on the usage location. Relative paths are allowed within the INSTALL_INTERFACE expression and are interpreted as relative to the installation prefix. Relative paths should not be used in BUILD_INTERFACE expressions because they will not be converted to absolute. For example:

```
target_include_directories(mylib PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include/mylib>
  $<INSTALL_INTERFACE:include/mylib>  # <prefix>/include/mylib
)
```

