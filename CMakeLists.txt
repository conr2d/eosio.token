cmake_minimum_required(VERSION 3.16)
project(eosio.token)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(clsdk REQUIRED)

add_executable(eosio.token src/eosio.token.cpp)
target_include_directories(eosio.token PUBLIC include)
target_link_libraries(eosio.token eosio-contract-simple-malloc)

execute_process(COMMAND ln -sf ${clsdk_DIR} ${CMAKE_CURRENT_BINARY_DIR}/clsdk)
execute_process(COMMAND ln -sf ${WASI_SDK_PREFIX} ${CMAKE_CURRENT_BINARY_DIR}/wasi-sdk)

set(CMAKE_EXPORT_COMPILE_COMMANDS on)
