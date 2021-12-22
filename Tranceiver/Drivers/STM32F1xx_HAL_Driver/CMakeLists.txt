file(GLOB Headers Inc/*.h Inc/Legacy/*.h)
file(GLOB Sources Src/*.c)

list(FILTER Sources EXCLUDE REGEX ".*_template.c")

add_library(HAL STATIC ${Headers} ${Sources})

target_include_directories(HAL PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/Inc ${CMAKE_CURRENT_SOURCE_DIR}/Inc/Legacy)
target_include_directories(HAL PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/../../Core/Inc)