add_library(scriptbuilder STATIC
    scriptbuilder.cpp
    scriptbuilder.h
)

target_include_directories(scriptbuilder PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)

