add_library(WebRGB INTERFACE)

target_sources(WebRGB INTERFACE
  ${CMAKE_CURRENT_LIST_DIR}/pico_neopixel_animations.cpp
)

# Include the Neopixel directory
add_subdirectory(pico_neopixels)

# Enable USB, UART output
pico_enable_stdio_usb(WebRGB 1)
pico_enable_stdio_uart(WebRGB 0)

# Include files in the current directory
target_include_directories(WebRGB INTERFACE ${CMAKE_CURRENT_LIST_DIR})

# Link the Project to libraries (cyw43_arch, pico_stdlib)
target_link_libraries(
        WebRGB INTERFACE
        pico_stdlib
        pico_neopixel
        )
