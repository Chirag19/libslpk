# bump version here
set(slpk_VERSION 1.2)

define_module(LIBRARY slpk=${slpk_VERSION}
  DEPENDS roarchive>=1.8 geo>=1.26 imgproc>=1.20 geometry>=1.9
  math>=1.2 utility>=1.19 dbglog>=1.4
  jsoncpp>=2.3
  Boost_FILESYSTEM
  JPEG # need to measure JPEG images
  )

set(slpk_SOURCES
  reader.hpp reader.cpp
  writer.hpp writer.cpp
  restapi.hpp
)

add_library(slpk STATIC ${slpk_SOURCES})
buildsys_library(slpk)

target_link_libraries(slpk ${MODULE_LIBRARIES})
buildsys_target_compile_definitions(slpk ${MODULE_DEFINITIONS})

if(MODULE_service_FOUND)
  add_subdirectory(tools EXCLUDE_FROM_ALL)
endif()
