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

