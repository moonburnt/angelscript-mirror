add_library(scriptstdstring STATIC
    scriptstdstring_utils.cpp
    scriptstdstring.cpp
    scriptstdstring.h
)

target_include_directories(scriptstdstring PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
