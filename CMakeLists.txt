cmake_minimum_required(VERSION 3.0.0)
project(Reduction CXX CUDA)

include_directories(/home/mjdyx/Documents/C++/include)
include_directories(/usr/local/cuda-11.1/include)
add_compile_options(--std c++17)


# add_compile_options(-march=native)
# include(CTest)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
	set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin/Debug)
else()
	set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin/Release)
endif()


add_executable(Reduction Reduction.cu)
target_compile_options(Reduction PRIVATE $<$<COMPILE_LANGUAGE:CUDA>:-gencode arch=compute_86,code=sm_86>)
# set_target_properties(Reduction PROPERTIES CUDA_ARCHITECTURES 86)
set_target_properties(Reduction PROPERTIES CUDA_SEPARABLE_COMPILATION ON)