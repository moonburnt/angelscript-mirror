add_library(scriptmath STATIC
    scriptmath.cpp
    scriptmath.h
    scriptmathcomplex.cpp
    scriptmathcomplex.h
)

target_include_directories(scriptmath PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)

