cmake_minimum_required(VERSION 3.5)

project(angelscript)

option(BUILD_SHARED_LIBS "Build shared library" OFF)
option(ANGELSCRIPT_AS_NO_EXCEPTIONS "Disable exception handling in script context" OFF)
option(ANGELSCRIPT_WITH_ADDONS "Compile angelscript's addons and include their headers" ON)

if(MSVC)
    option(MSVC_COMPILE_FLAGS "Compiler flags to use with MSVC" "/MP")
endif()

if(APPLE)
    option(BUILD_FRAMEWORK "Build Framework bundle for OSX" OFF)
endif()

file(READ include/angelscript.h ANGELSCRIPT_H)
string(REGEX MATCH "#define ANGELSCRIPT_VERSION_STRING \"([0-9]*).([0-9]*).([0-9]*)" ANGELSCRIPT_VERSION_REGEX ${ANGELSCRIPT_H})
set(ANGELSCRIPT_VERSION_MAJOR ${CMAKE_MATCH_1})
set(ANGELSCRIPT_VERSION_MINOR ${CMAKE_MATCH_2})
set(ANGELSCRIPT_VERSION_PATCH ${CMAKE_MATCH_3})
set(PROJECT_VERSION ${ANGELSCRIPT_VERSION_MAJOR}.${ANGELSCRIPT_VERSION_MINOR}.${ANGELSCRIPT_VERSION_PATCH})

set(CMAKE_POSITION_INDEPENDENT_CODE TRUE)

set(ARCHFLAGS "${CMAKE_SYSTEM_PROCESSOR}")
if (APPLE AND NOT IOS)
  if (${CMAKE_SYSTEM_PROCESSOR} MATCHES "arm")
    set(ARCHFLAGS "aarch64")
  endif ()
endif ()

message(STATUS "Configuring angelscript ${PROJECT_VERSION}")

find_package(Threads)

if(NOT BUILD_FRAMEWORK)
    set(ANGELSCRIPT_LIBRARY_NAME angelscript)
else()
    set(ANGELSCRIPT_LIBRARY_NAME Angelscript) # OS X frameworks should have capitalized name
    set(BUILD_SHARED_LIBS TRUE)
endif()

add_library(${ANGELSCRIPT_LIBRARY_NAME})

target_sources(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE
    include/angelscript.h
    source/as_array.h
    source/as_builder.h
    source/as_bytecode.h
    source/as_callfunc.h
    source/as_compiler.h
    source/as_config.h
    source/as_configgroup.h
    source/as_context.h
    source/as_criticalsection.h
    source/as_datatype.h
    source/as_debug.h
    source/as_generic.h
    source/as_map.h
    source/as_memory.h
    source/as_module.h
    source/as_objecttype.h
    source/as_outputbuffer.h
    source/as_parser.h
    source/as_property.h
    source/as_restore.h
    source/as_scriptcode.h
    source/as_scriptengine.h
    source/as_scriptfunction.h
    source/as_scriptnode.h
    source/as_scriptobject.h
    source/as_string.h
    source/as_string_util.h
    source/as_texts.h
    source/as_thread.h
    source/as_tokendef.h
    source/as_tokenizer.h
    source/as_typeinfo.h
    source/as_variablescope.h

    source/as_atomic.cpp
    source/as_builder.cpp
    source/as_bytecode.cpp
    source/as_callfunc.cpp
    source/as_callfunc_mips.cpp
    source/as_callfunc_x86.cpp
    source/as_callfunc_x64_gcc.cpp
    source/as_callfunc_x64_msvc.cpp
    source/as_callfunc_x64_mingw.cpp
    source/as_compiler.cpp
    source/as_configgroup.cpp
    source/as_context.cpp
    source/as_datatype.cpp
    source/as_gc.cpp
    source/as_generic.cpp
    source/as_globalproperty.cpp
    source/as_memory.cpp
    source/as_module.cpp
    source/as_objecttype.cpp
    source/as_outputbuffer.cpp
    source/as_parser.cpp
    source/as_restore.cpp
    source/as_scriptcode.cpp
    source/as_scriptengine.cpp
    source/as_scriptfunction.cpp
    source/as_scriptnode.cpp
    source/as_scriptobject.cpp
    source/as_string.cpp
    source/as_string_util.cpp
    source/as_thread.cpp
    source/as_tokenizer.cpp
    source/as_typeinfo.cpp
    source/as_variablescope.cpp
)

if(MSVC AND CMAKE_CL_64)
    enable_language(ASM_MASM)
    if(CMAKE_ASM_MASM_COMPILER_WORKS)
        target_sources(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE
            source/as_callfunc_x64_msvc_asm.asm
        )
    else()
        message(FATAL ERROR "MSVC x86_64 target requires a working assembler")
    endif()
endif()

if(${ARCHFLAGS} MATCHES "^arm")
    enable_language(ASM)
    if(CMAKE_ASM_COMPILER_WORKS)
        target_sources(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE
            source/as_callfunc_arm.cpp
            source/as_callfunc_arm_gcc.S
        )
        set_property(SOURCE source/as_callfunc_arm_gcc.S APPEND PROPERTY COMPILE_FLAGS " -Wa,-mimplicit-it=always")
    else()
        message(FATAL ERROR "ARM target requires a working assembler")
    endif()
endif()

if(${ARCHFLAGS} MATCHES "^aarch64")
    enable_language(ASM)
    if(CMAKE_ASM_COMPILER_WORKS)
        target_sources(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE
            source/as_callfunc_arm64.cpp
            source/as_callfunc_arm64_gcc.S
        )
        #set_property(SOURCE source/as_callfunc_arm64_gcc.S APPEND PROPERTY COMPILE_FLAGS " -Wa")
    else()
        message(FATAL ERROR "ARM target requires a working assembler")
    endif()
endif()

if(MSVC)
    set(CMAKE_DEBUG_POSTFIX "d")
endif()

set(ANGELSCRIPT_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_include_directories(${ANGELSCRIPT_LIBRARY_NAME}
    PRIVATE
        ${ANGELSCRIPT_INCLUDE_DIR}
)

if(MSVC)
    target_compile_definitions(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE
        -D_CRT_SECURE_NO_WARNINGS
    )
endif()

target_compile_definitions(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE
    -DANGELSCRIPT_EXPORT
    -D_LIB
)

if(ANGELSCRIPT_AS_NO_EXCEPTIONS)
    target_compile_definitions(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE AS_NO_EXCEPTIONS)
endif()

# Don't override the default library output path to avoid conflicts when building for multiple target platforms
#set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
target_link_libraries(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE Threads::Threads)

set_target_properties(${ANGELSCRIPT_LIBRARY_NAME} PROPERTIES VERSION ${PROJECT_VERSION})

if(BUILD_FRAMEWORK)
    set_target_properties(${ANGELSCRIPT_LIBRARY_NAME} PROPERTIES
        FRAMEWORK TRUE
        FRAMEWORK_VERSION ${PROJECT_VERSION}
        MACOSX_FRAMEWORK_IDENTIFIER com.angelcode.Angelscript
        MACOSX_FRAMEWORK_SHORT_VERSION_STRING ${PROJECT_VERSION}
        MACOSX_FRAMEWORK_BUNDLE_VERSION ${PROJECT_VERSION}
        XCODE_ATTRIBUTE_INSTALL_PATH "@rpath"
        PUBLIC_HEADER include/angelscript.h
    )
endif()

if(MSVC AND MSVC_COMPILE_FLAGS)
    target_compile_options(${ANGELSCRIPT_LIBRARY_NAME} PRIVATE "${MSVC_COMPILE_FLAGS}")
endif()

# Don't override the default runtime output path to avoid conflicts when building for multiple target platforms
#set(RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

if(ANGELSCRIPT_WITH_ADDONS)
    add_subdirectory(add_on)
    target_link_libraries(angelscript PRIVATE addons)
endif()
