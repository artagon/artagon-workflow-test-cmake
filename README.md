# Artagon Workflow Test - CMake C/C++

[![CI](https://github.com/artagon/artagon-workflow-test-cmake/actions/workflows/ci.yml/badge.svg)](https://github.com/artagon/artagon-workflow-test-cmake/actions/workflows/ci.yml)

Test repository for validating [artagon-workflows](https://github.com/artagon/artagon-workflows) CMake C and C++ CI reusable workflows.

## Purpose

Validates that `cmake_c_ci.yml` and `cmake_cpp_ci.yml` reusable workflows:
- Build CMake projects correctly for C and C++
- Run tests and report results
- Support different language standards (C11/17/23, C++17/20/23)
- Handle custom CMake options
- Generate code coverage
- Work across Linux, macOS, Windows

## Test Matrix

### C Tests

| Test | Standard | Custom Options |
|------|----------|----------------|
| Default | 17 | - |
| C11 | 11 | - |
| C17 | 17 | - |
| C23 | 23 | - |
| Custom | 17 | `-DCMAKE_VERBOSE_MAKEFILE=ON` |

### C++ Tests

| Test | Standard |
|------|----------|
| Default | 20 |
| C++17 | 17 |
| C++20 | 20 |
| C++23 | 23 |

## Project Structure

```
.
├── CMakeLists.txt          # C project configuration
├── src/
│   ├── main.c              # C main source
│   └── test.c              # C test source
├── cpp/                    # C++ project
│   ├── CMakeLists.txt
│   └── src/
│       ├── main.cpp
│       └── test.cpp
└── .github/workflows/
    └── ci.yml
```

## Triggers

- **Push to main** - Validates changes
- **Pull requests** - Pre-merge validation
- **Daily schedule** (2 AM UTC) - Catch upstream breaking changes
- **Manual dispatch** - On-demand testing
- **Repository dispatch** - Triggered by [trigger_test_repos.yml](https://github.com/artagon/artagon-workflows/blob/main/.github/workflows/trigger_test_repos.yml)

## Running Locally

### C Project

```bash
mkdir build && cd build
cmake ..
cmake --build .
ctest
```

### C++ Project

```bash
cd cpp
mkdir build && cd build
cmake ..
cmake --build .
ctest
```

## Related

- [artagon-workflows](https://github.com/artagon/artagon-workflows) - Main workflow repository
- [cmake_c_ci.yml](https://github.com/artagon/artagon-workflows/blob/main/.github/workflows/cmake_c_ci.yml) - C workflow
- [cmake_cpp_ci.yml](https://github.com/artagon/artagon-workflows/blob/main/.github/workflows/cmake_cpp_ci.yml) - C++ workflow
- [Testing Guide](https://github.com/artagon/artagon-workflows/blob/main/docs/TESTING.md)
