add_library(contextmgr STATIC
    contextmgr.cpp
    contextmgr.h
)

target_include_directories(contextmgr PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
