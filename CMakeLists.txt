project(nrf51-sdk)

include("${CODAL_UTILS_LOCATION}")

# find sources and headers
RECURSIVE_FIND_DIR(TOP_LEVEL_INCLUDE_DIRS "${CMAKE_CURRENT_SOURCE_DIR}/source" "*.h")
RECURSIVE_FIND_FILE(TOP_LEVEL_SOURCE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/source" "*.c??")

include_directories(${TOP_LEVEL_INCLUDE_DIRS})

# create our target
add_library(nrf51-sdk ${TOP_LEVEL_SOURCE_FILES})

target_link_libraries(
    nrf51-sdk
    ble
)

# expose it to parent cmake.
target_include_directories(nrf51-sdk PUBLIC ${TOP_LEVEL_INCLUDE_DIRS})