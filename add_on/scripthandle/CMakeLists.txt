add_library(scripthandle STATIC
    scripthandle.cpp
    scripthandle.h
)

target_include_directories(scripthandle PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)


