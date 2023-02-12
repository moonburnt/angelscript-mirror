add_library(autowrapper INTERFACE
    # I assume, this generator is meant to be built separately
    # generator/generateheader.cpp
    aswrappedcall.h
)

set_target_properties(autowrapper PROPERTIES LINKER_LANGUAGE CXX)

target_include_directories(autowrapper INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${ANGELSCRIPT_INCLUDE_DIR}
)
