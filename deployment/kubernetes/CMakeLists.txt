set(service "pv")
include("${CMAKE_SOURCE_DIR}/script/service.cmake")
include("${CMAKE_SOURCE_DIR}/script/scan-all.cmake")
add_custom_target(volume ${CMAKE_CURRENT_SOURCE_DIR}/mkvolume.sh)

# add cleanup files
file(GLOB m4files "${CMAKE_CURRENT_SOURCE_DIR}/*.yaml.m4")
foreach(m4file ${m4files})
    string(REPLACE ".yaml.m4" ".yaml" yamlfile "${m4file}")
    set_property(DIRECTORY APPEND PROPERTY ADDITIONAL_MAKE_CLEAN_FILES "${yamlfile}")
endforeach(m4file)
