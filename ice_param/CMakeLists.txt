set(iceparam_src
  ice_albedo.F90 ocean_albedo.F90 ocean_rough.F90)

list(TRANSFORM iceparam_src PREPEND src/)

add_library(iceparam_cpl ${iceparam_src})
target_link_libraries(iceparam_cpl FMS::fms_r8)

set_target_properties(iceparam_cpl PROPERTIES
  Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/include
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_BINARY_DIR}/include)
