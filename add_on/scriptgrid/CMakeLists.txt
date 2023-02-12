add_library(scriptgrid STATIC
    scriptgrid.cpp
    scriptgrid.h
)

target_include_directories(scriptgrid PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)

