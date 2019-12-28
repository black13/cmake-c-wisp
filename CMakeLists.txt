# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)
project(wisp C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS}")   # Add more flags here

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/CMake/Modules)
find_package(GMP REQUIRED)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/out")


INCLUDE_DIRECTORIES(
    "${GMP_INCLUDES}"
    "${CMAKE_SOURCE_DIR}"
)

set(SOURCE_FILES main.c common.c cons.c detach.c hashtab.c  number.c lisp_math.c mem.c lisp.c common.c detach.c object.c str.c reader.c vector.c
cons.c eval.c symtab.c)
add_executable(wisp ${SOURCE_FILES} )

target_link_libraries(wisp ${GMP_LIBRARIES})