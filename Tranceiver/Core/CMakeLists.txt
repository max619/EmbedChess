file(GLOB Headers Inc/*.h)
file(GLOB Sources Src/*.c)

add_executable(Tranceiver ${Headers} ${Sources} ${CMAKE_CURRENT_SOURCE_DIR}/../startup_stm32f103xb.s)

target_link_libraries(Tranceiver PRIVATE HAL)

target_include_directories(Tranceiver PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/Inc)

add_custom_command(TARGET Tranceiver
                   POST_BUILD
                   COMMAND ${SZ_EXE} $<TARGET_FILE:Tranceiver>
                   COMMAND ${OBJCOPY_EXE} -O ihex $<TARGET_FILE:Tranceiver> ${CMAKE_CURRENT_BINARY_DIR}/$<TARGET_FILE_BASE_NAME:Tranceiver>.hex
                   COMMAND ${OBJCOPY_EXE} -O binary -S $<TARGET_FILE:Tranceiver> ${CMAKE_CURRENT_BINARY_DIR}/$<TARGET_FILE_BASE_NAME:Tranceiver>.bin
                   VERBATIM
                   )