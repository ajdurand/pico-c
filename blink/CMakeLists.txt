cmake_minimum_required(VERSION 3.13)

set (FNAME "blink")

include(pico_sdk_import.cmake)

project(${FNAME} C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

#set(CMAKE_ASM_COMPILER arm-none-eabi-gcc)

pico_sdk_init()

add_compile_options(-Wall
        -Wno-format          # int != int32_t as far as the compiler is concerned because gcc has int32_t as long int
        -Wno-unused-function # we have some for the docs that aren't called
        -Wno-maybe-uninitialized
        )

add_executable(${FNAME}
	${FNAME}.c
	)

target_link_libraries(${FNAME} pico_stdlib)
pico_add_extra_outputs(${FNAME})
