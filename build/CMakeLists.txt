cmake_minimum_required(VERSION 3.15)
set(CMAKE_SYSTEM_NAME Generic)
set(CMAKE_C_COMPILER arm-none-eabi-gcc)
set(CMAKE_C_COMPILER_WORKS 1)
set(CMAKE_C_FLAGS "-Os -g")
set(CMAKE_C_FLAGS_DEBUG "-Og")
project(ESCape32 C)
if(UNIX AND NOT CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT) # Use 'CMAKE_INSTALL_PREFIX' as alternative system root
	set(CMAKE_PREFIX_PATH ${CMAKE_INSTALL_PREFIX})
	include(GNUInstallDirs)
	include_directories(${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_INCLUDEDIR})
	link_directories(${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR})
endif()
if(LIBOPENCM3_DIR)
	include_directories(${LIBOPENCM3_DIR}/include)
	link_directories(${LIBOPENCM3_DIR}/lib)
endif()
add_compile_options(-ffreestanding -ffunction-sections -fdata-sections -fsingle-precision-constant
	-Wall -Wextra -Wpedantic -Wundef -Wshadow -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes
	-Wno-variadic-macros -Wno-unused-result -Wno-unused-parameter -Wno-unused-label)
add_link_options(-nostartfiles -Wl,--gc-sections)

function(add_target name mcu)
	include(mcu/${mcu}/config.cmake)
	file(READ src/main.c main_c)
	string(REGEX MATCH "REVISION [0-9]+" rev ${main_c})
	string(REGEX REPLACE "[^0-9]+" "-rev" rev ${rev})
	set(elf ${name}${rev}.elf)
	set(bin ${name}${rev}.bin)
	set(hex ${name}${rev}.hex)
	file(GLOB srcs src/*.c mcu/${mcu}/*.c)
	add_executable(${elf} ${srcs})
	target_include_directories(${elf} PRIVATE src mcu/${mcu})
	target_compile_options(${elf} PRIVATE ${opts})
	target_compile_definitions(${elf} PRIVATE ${mcu} ${name} ${defs} TARGET_NAME="${name}" ${ARGN})
	target_link_options(${elf} PRIVATE -T${CMAKE_CURRENT_SOURCE_DIR}/mcu/${mcu}/config.ld -T${CMAKE_CURRENT_SOURCE_DIR}/mcu/common.ld ${opts})
	target_link_libraries(${elf} c_nano gcc nosys ${libs})
	add_custom_command(
		OUTPUT ${bin} ${hex}
		COMMAND arm-none-eabi-objcopy -O binary ${elf} ${bin}
		COMMAND arm-none-eabi-objcopy -O ihex ${elf} ${hex}
		DEPENDS ${elf}
	)
	add_custom_target(${name} ALL DEPENDS ${hex})
	add_custom_target(flash-${name} COMMAND st-flash --reset --connect-under-reset --format ihex write ${hex} DEPENDS ${hex})
endfunction()

add_subdirectory(boot)

add_target(REMORA_198_2178 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=198 ANALOG_MAX=2178 FULL_DUTY DUTY_MIN=90 DUTY_MAX=100 DUTY_SPUP=25 DUTY_RAMP=0 DUTY_RATE=25) # 1.1 - 12.1V

add_target(REMORA_180_2142 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=180 ANALOG_MAX=2142 FULL_DUTY DUTY_MIN=90 DUTY_MAX=100 DUTY_SPUP=25 DUTY_RAMP=0 DUTY_RATE=25) # 1 - 11.9V

add_target(REMORA_180_1440 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=180 ANALOG_MAX=1440 FULL_DUTY DUTY_MIN=90 DUTY_MAX=100 DUTY_SPUP=25 DUTY_RAMP=0 DUTY_RATE=25) # 1 - 8V

add_target(REMORA_369_2178 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=369 ANALOG_MAX=2178 FULL_DUTY DUTY_MIN=100) # 2.05 - 12.1V

add_target(REMORA_540_1803 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX FULL_DUTY ANALOG_MIN=540 ANALOG_MAX=1803 DUTY_MIN=100) # 3 - 10V
add_target(REMORA_396_1803 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX FULL_DUTY ANALOG_MIN=396 ANALOG_MAX=1803 DUTY_MIN=100) # 2.2 - 10V

add_target(REMORA_342_1800 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX FULL_DUTY ANALOG_MIN=360 ANALOG_MAX=1803 DUTY_MIN=100) # 2 - 10V
add_target(REMORA_324_1800 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX FULL_DUTY ANALOG_MIN=324 ANALOG_MAX=1803 DUTY_MIN=100) # 1.8 - 10V
add_target(REMORA_216_1442 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX FULL_DUTY ANALOG_MIN=216 ANALOG_MAX=1442 DUTY_MIN=100) # 1.2 - 8V

add_target(MA_1 AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=180 ANALOG_MAX=1440 FULL_DUTY DUTY_MIN=90 sDUTY_MAX=100 DUTY_SPUP=25 DUTY_RAMP=0 DUTY_RATE=25) # 1 - 8V

