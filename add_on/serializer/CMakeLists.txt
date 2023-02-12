add_library(serializer STATIC
    serializer.cpp
    serializer.h
)

target_include_directories(serializer PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
