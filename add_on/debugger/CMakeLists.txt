add_library(debugger STATIC
    debugger.cpp
    debugger.h
)

target_include_directories(debugger PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
