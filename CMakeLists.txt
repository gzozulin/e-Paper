cmake_minimum_required(VERSION 3.2)
project(epaper C)

set(CMAKE_C_STANDARD 99)

file(GLOB_RECURSE SRC_FILES
        RaspberryPi_JetsonNano/c/examples/*.c
        RaspberryPi_JetsonNano/c/lib/e-Paper/*.c
        RaspberryPi_JetsonNano/c/lib/Fonts/*.c
        RaspberryPi_JetsonNano/c/lib/GUI/*.c)
list(APPEND SRC_FILES
        RaspberryPi_JetsonNano/c/lib/Config/dev_hardware_SPI.c
        RaspberryPi_JetsonNano/c/lib/Config/RPI_sysfs_gpio.c
        RaspberryPi_JetsonNano/c/lib/Config/DEV_Config.c)

#[[add_executable(binepaper ${SRC_FILES})
add_compile_definitions(DEBUG RPI USE_WIRINGPI_LIB)
target_include_directories(binepaper PUBLIC RaspberryPi_JetsonNano/c/examples)
target_include_directories(binepaper PUBLIC RaspberryPi_JetsonNano/c/lib/Config)
target_include_directories(binepaper PUBLIC RaspberryPi_JetsonNano/c/lib/e-Paper)
target_include_directories(binepaper PUBLIC RaspberryPi_JetsonNano/c/lib/Fonts)
target_include_directories(binepaper PUBLIC RaspberryPi_JetsonNano/c/lib/GUI)
target_link_libraries(binepaper PUBLIC wiringPi m)]]

add_library(epaper ${SRC_FILES})
add_compile_definitions(DEBUG RPI USE_WIRINGPI_LIB)
target_include_directories(epaper PUBLIC RaspberryPi_JetsonNano/c/examples)
target_include_directories(epaper PUBLIC RaspberryPi_JetsonNano/c/lib/Config)
target_include_directories(epaper PUBLIC RaspberryPi_JetsonNano/c/lib/e-Paper)
target_include_directories(epaper PUBLIC RaspberryPi_JetsonNano/c/lib/Fonts)
target_include_directories(epaper PUBLIC RaspberryPi_JetsonNano/c/lib/GUI)
target_link_libraries(epaper PUBLIC wiringPi)