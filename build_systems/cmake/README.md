# CMake Integration

Use this directory to integrate `tincup` with CMake-based projects.

## Quick Start

```bash
# From your project root
cmake -S . -B build
cmake --build build
```

## Integration with Your Project

### FetchContent (top-level entrypoint)

Add this to your `CMakeLists.txt`:

```cmake
include(FetchContent)

FetchContent_Declare(
  tincup
  GIT_REPOSITORY https://github.com/sandialabs/TInCuP.git
  GIT_TAG        main
  SOURCE_SUBDIR  build_systems/cmake  # Important: point to this subdirectory
)

FetchContent_MakeAvailable(tincup)

# Link to your target
target_link_libraries(your_target PRIVATE tincup::tincup)
```

### Installed Package

Add this to your `CMakeLists.txt`:

```cmake
find_package(tincup CONFIG REQUIRED)

# Link to your target
target_link_libraries(your_target PRIVATE tincup::tincup)
```

## What's Included

- Header-only library target: `tincup::tincup`
- Include path: `include/tincup/tincup.hpp`
- C++20 requirement enforcement
- Modern CMake best practices
