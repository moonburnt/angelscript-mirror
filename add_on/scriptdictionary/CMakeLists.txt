add_library(scriptdictionary STATIC
    scriptdictionary.cpp
    scriptdictionary.h
)

target_include_directories(scriptdictionary PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
