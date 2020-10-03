cmake_minimum_required(VERSION 3.16)

project(cufhe LANGUAGES CXX CUDA)

set(CMAKE_CXX_STANDARD 17)

include_directories(.)

add_library(cufhe_cpu SHARED
            lib/cufhe.cc
            lib/cufhe_cpu.cc
            lib/cufhe_io.cc
            lib/cufhe_gates_cpu.cc
            lib/bootstrap_cpu.cc      
            lib/details/allocator_cpu.cc        
)       

add_executable(cufhe_test_cpu test/test_api_cpu.cc)

target_link_libraries(cufhe_test_cpu cufhe_cpu)

add_library(cufhe_gpu SHARED
            lib/cufhe.cc 
            lib/cufhe_io.cc
            lib/cufhe_gpu.cu
            lib/bootstrap_gpu.cu
            lib/cufhe_gates_gpu.cu
            lib/details/allocator_gpu.cu
            lib/ntt_gpu/ntt_1024_twiddle.cu)

add_executable(cufhe_test_gpu test/test_api_gpu.cu)

target_link_libraries(cufhe_test_gpu cufhe_gpu)