add_library(scriptfile STATIC
    scriptfile.cpp
    scriptfile.h
    scriptfilesystem.cpp
    scriptfilesystem.h
)

target_include_directories(scriptfile PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
