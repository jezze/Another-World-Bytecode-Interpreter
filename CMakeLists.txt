set(CMAKE_SYSTEM_NAME Linux)
set(CMAKE_SYSTEM_PROCESSOR mips)

set(tools /home/jfu/x-tools/gcw0-toolchain)
set(CMAKE_C_COMPILER ${tools}/bin/mipsel-gcw0-linux-uclibc-gcc)
set(CMAKE_CXX_COMPILER ${tools}/bin/mipsel-gcw0-linux-uclibc-g++)

cmake_minimum_required(VERSION 3.13)
project(raw)

set(CMAKE_CXX_STANDARD 11)

add_definitions(-DAUTO_DETECT_PLATFORM)
add_definitions(-DBYPASS_PROTECTION)
set(CMAKE_CXX_FLAGS " -Os -g -fno-rtti -fno-exceptions -Wall -Wno-unknown-pragmas -Wshadow -Wundef -Wwrite-strings -Wnon-virtual-dtor -Wno-multichar")

add_executable(raw
        src/bank.cpp
        src/engine.cpp
        src/file.cpp
        src/main.cpp
        src/mixer.cpp
        src/parts.cpp
        src/resource.cpp
        src/serializer.cpp
        src/sfxplayer.cpp
        src/staticres.cpp
        src/sysImplementation.cpp
        src/util.cpp
        src/video.cpp
        src/vm.cpp
)

find_package(SDL2 REQUIRED)
target_link_libraries(raw SDL2)
target_link_libraries(raw z)
