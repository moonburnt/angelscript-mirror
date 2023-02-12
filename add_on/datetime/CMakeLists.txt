add_library(datetime STATIC
    datetime.cpp
    datetime.h
)

target_include_directories(datetime PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
