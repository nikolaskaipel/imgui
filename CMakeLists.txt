cmake_minimum_required(VERSION 3.15)
project(imgui)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(IMGUI_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

set(IMGUI_SRC
        "${IMGUI_DIR}/imgui.cpp"
        "${IMGUI_DIR}/imgui.h"
        "${IMGUI_DIR}/imgui_draw.cpp"
        "${IMGUI_DIR}/imgui_tables.cpp"
        "${IMGUI_DIR}/imgui_widgets.cpp"
        "${IMGUI_DIR}/imgui_demo.cpp"
        "${IMGUI_DIR}/backends/imgui_impl_dx12.cpp"
        "${IMGUI_DIR}/backends/imgui_impl_dx12.h"
        "${IMGUI_DIR}/backends/imgui_impl_win32.cpp"
        "${IMGUI_DIR}/backends/imgui_impl_win32.h"
)

add_library(${PROJECT_NAME} STATIC ${IMGUI_SRC})

target_include_directories(${PROJECT_NAME} PRIVATE
    ${IMGUI_DIR}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    d3d12.lib
    dxgi.lib
    d3dcompiler.lib
    user32.lib
)
