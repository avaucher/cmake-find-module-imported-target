# CMake Find Modules with Imported Targets

For many commonly-used libraries, one can find CMake find modules easily on the web.
However, many of those find modules only define variables for the include directories and libraries - a project using such a library must then manually set those dependencies in the following fashion:

```CMake
find_package(XXX REQUIRED)
target_include_directories(MyTarget PUBLIC ${XXX_INCLUDE_DIRS})
target_link_libraries(MyTarget PUBLIC ${XXX_LIBRARIES})
```

Nevertheless, modern CMake allows for use of imported targets, which simplifies the above to:

```CMake
find_package(XXX REQUIRED)
target_link_libraries(MyTarget PUBLIC XXX::XXX)
```

In addition to be shorter than the previous version, a big advantage is that it makes `MyTarget` independent of the specific installation of `XXX` when installing `MyTarget` as a CMake package ([here](https://cmake.org/cmake/help/latest/manual/cmake-packages.7.html#creating-packages) for details).

## Available Find modules

Many libraries already define imported targets and are not included in this project.

Find modules:
* [TBB](cmake/FindTBB.cmake)
* [Cairo](cmake/FindCairo.cmake)
