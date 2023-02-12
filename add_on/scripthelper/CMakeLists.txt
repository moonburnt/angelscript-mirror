add_library(scripthelper STATIC
    scripthelper.cpp
    scripthelper.h
)

target_include_directories(scripthelper PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
