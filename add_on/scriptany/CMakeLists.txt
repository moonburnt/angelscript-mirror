add_library(scriptany STATIC
    scriptany.cpp
    scriptany.h
)

target_include_directories(scriptany PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
