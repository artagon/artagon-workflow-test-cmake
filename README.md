# Artagon Workflows - CMake C/C++ CI Test Repository

This repository tests the [artagon-workflows](https://github.com/artagon/artagon-workflows) CMake C and C++ CI reusable workflows.

## Purpose

Validates that the `cmake_c_ci.yml` and `cmake_cpp_ci.yml` reusable workflows:
- Build CMake projects correctly for C and C++
- Run tests and report results
- Support different language standards (C11/17/23, C++17/20/23)
- Handle custom CMake options
- Upload build artifacts
- Work with various configurations

## Test Matrix

### C Tests

| Test | Standard | Custom Options | Tests |
|------|----------|----------------|-------|
| Default | 17 | - | ✓ |
| C11 | 11 | - | ✓ |
| C17 | 17 | - | ✓ |
| C23 | 23 | - | ✓ |
| Custom | 17 | `-DCMAKE_VERBOSE_MAKEFILE=ON` | ✓ |

### C++ Tests

| Test | Standard | Source Dir | Tests |
|------|----------|------------|-------|
| Default | 20 | cpp | ✓ |
| C++17 | 17 | cpp | ✓ |
| C++20 | 20 | cpp | ✓ |
| C++23 | 23 | cpp | ✓ |

## Triggers

This workflow runs on:
- **Push to main** - Validates changes to this test repo
- **Pull requests** - Validates PRs before merge
- **Daily schedule** (2 AM UTC) - Catches breaking changes in artagon-workflows
- **Manual dispatch** - On-demand testing with custom standards
- **Repository dispatch** - Triggered by artagon-workflows on releases/updates

## Project Structure

```
.
├── CMakeLists.txt          # CMake configuration for C project
├── src/
│   ├── main.c              # C main source
│   └── test.c              # C test source
├── cpp/                    # C++ project
│   ├── CMakeLists.txt      # CMake configuration for C++ project
│   └── src/
│       ├── main.cpp        # C++ main source
│       └── test.cpp        # C++ test source
└── .github/
    └── workflows/
        └── ci.yml          # Workflow testing configuration
```

## Test Projects

### C Project
- **Language**: C17
- **Build System**: CMake 3.20+
- **Tests**: Simple assertion-based tests

### C++ Project
- **Language**: C++20
- **Build System**: CMake 3.20+
- **Tests**: Simple assertion-based tests

## Running Locally

### C Project

```bash
# Build and test
mkdir build && cd build
cmake ..
cmake --build .
ctest

# Clean
cd .. && rm -rf build
```

### C++ Project

```bash
# Build and test
cd cpp
mkdir build && cd build
cmake ..
cmake --build .
ctest

# Clean
cd .. && rm -rf build
```

## Related

- [artagon-workflows](https://github.com/artagon/artagon-workflows) - Main workflow repository
- [CMake C CI Workflow](https://github.com/artagon/artagon-workflows/blob/main/.github/workflows/cmake_c_ci.yml) - C workflow being tested
- [CMake C++ CI Workflow](https://github.com/artagon/artagon-workflows/blob/main/.github/workflows/cmake_cpp_ci.yml) - C++ workflow being tested
- [Testing Strategy](https://github.com/artagon/artagon-workflows/blob/main/.model-context/TESTING_STRATEGY.md) - Overall testing approach
