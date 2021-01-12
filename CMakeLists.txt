cmake_minimum_required(VERSION 3.17)
project(untitled1)
set(CMAKE_CXX_STANDARD 14)

find_package(LLVM REQUIRED CONFIG)
message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

add_executable(untitled1 main.cpp KaleidoscopeJIT.h)


# Find the libraries that correspond to the LLVM components
# that we wish to use
llvm_map_components_to_libnames(all)

# Link against LLVM libraries
target_link_libraries(untitled1 ${llvm_libs})