cmake_minimum_required(VERSION 3.20)

project(Transciever)

enable_language(C CXX ASM)

SET(CMAKE_EXECUTABLE_SUFFIX .elf)

include_directories(Drivers/CMSIS/Device/ST/STM32F1xx/Include Drivers/CMSIS/Include)
add_definitions(-DUSE_HAL_DRIVER -DSTM32F103xB)

add_subdirectory(Drivers)
add_subdirectory(Core)