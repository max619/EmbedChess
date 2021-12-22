file(GLOB Headers Include/*.h)

add_library(CMSIS_STM32F1xx INTERFACE ${Headers})
target_include_directories(CMSIS_STM32F1xx INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/Include)
