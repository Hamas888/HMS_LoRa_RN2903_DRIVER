# HMS_LoRa_RN2903_DRIVER/CMakeLists.txt

set(HMS_LoRa_RN2903_DRIVER_VERSION 1.0.0)

# Check if we're building with Zephyr
if(DEFINED ZEPHYR_BASE)

    # zephyr_library()
    # zephyr_library_sources() → not needed yet
    zephyr_include_directories(include)

# Check if we're building with ESP-IDF
elseif(DEFINED ESP_PLATFORM OR DEFINED IDF_VER OR DEFINED ENV{IDF_PATH})
    idf_component_register(
        # SRCS "src/HMS_LoRa_RN2903_DRIVER.cpp" → not needed yet
        INCLUDE_DIRS "include"
        REQUIRES ""
    )
    
# STM32 / generic CMake project
else()
    add_library(HMS_LoRa_RN2903_DRIVER INTERFACE)
    target_include_directories(HMS_LoRa_RN2903_DRIVER INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)
    target_compile_features(HMS_LoRa_RN2903_DRIVER INTERFACE cxx_std_17)
endif()