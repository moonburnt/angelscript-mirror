list(APPEND ADDONS
    autowrapper
    contextmgr
    datetime
    debugger
    scriptany
    scriptarray
    scriptbuilder
    scriptdictionary
    scriptfile
    scriptgrid
    scripthandle
    scripthelper
    scriptmath
    scriptstdstring
    serializer
    weakref
)

set(ANGELSCRIPT_ADDON_LIST ${ADDONS} CACHE STRING "List of addons to build")
message(STATUS "List of addons: ${ANGELSCRIPT_ADDON_LIST}")

add_library(addons INTERFACE)

function(add_addon addon)
    add_subdirectory(${addon})
    target_link_libraries(addons INTERFACE ${addon})
endfunction()

foreach(ADDON IN LISTS ANGELSCRIPT_ADDON_LIST)
    add_addon(${ADDON})
endforeach()
