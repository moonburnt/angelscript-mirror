#cmake_minimum_required(VERSION 3.5)

#project(add_on)

#add_library(add_on LIBRARY)
#add_library(add_on STATIC)

# set(ADD_ONS
#     autowrapper
#     contextmgr
#     datetime
#     debugger
#     scriptany
#     scriptarray
#     scriptbuilder
#     scriptdictionary
#     scriptfile
#     scriptgrid
#     scripthandle
#     scripthelper
#     scriptmath
#     scriptstdstring
#     serializer
#     weakref
#     CACHE INTERNAL ""
# )
#string (REPLACE "    " ";" ADD_ONS "${ADD_ONS}")

#message(${ADD_ONS})

# foreach(ADD_ON IN LISTS ADD_ONS)
#     #message(${ADD_ON})
#     add_subdirectory(${ADD_ON})
# endforeach()

add_subdirectory(autowrapper)
add_subdirectory(contextmgr)
add_subdirectory(datetime)
add_subdirectory(debugger)
add_subdirectory(scriptany)
add_subdirectory(scriptarray)
add_subdirectory(scriptbuilder)
add_subdirectory(scriptdictionary)
add_subdirectory(scriptfile)
add_subdirectory(scriptgrid)
add_subdirectory(scripthandle)
add_subdirectory(scripthelper)
add_subdirectory(scriptmath)
add_subdirectory(scriptstdstring)
add_subdirectory(serializer)
add_subdirectory(weakref)

#target_link_libraries(add_on autowrapper)
#target_link_libraries(add_on contextmgr)
#target_link_libraries(add_on datetime)
#target_link_libraries(add_on debugger)
#target_link_libraries(add_on scriptany)
#target_link_libraries(add_on scriptarray)
#target_link_libraries(add_on scriptbuilder)
#target_link_libraries(add_on scriptdictionary)
#target_link_libraries(add_on scriptfile)
#target_link_libraries(add_on scriptgrid)
#target_link_libraries(add_on scripthandle)
#target_link_libraries(add_on scripthelper)
#target_link_libraries(add_on scriptmath)
#target_link_libraries(add_on scriptstdstring)
#target_link_libraries(add_on serializer)
#target_link_libraries(add_on weakref)

#link_directories(autowrapper, contextmgr, datetime, debugger, scriptany, scriptarray, scriptbuilder, scriptdictionary, scriptfile, scriptgrid, scripthandle, scripthelper, scriptmath, scriptstdstring, serializer, weakref)
