set(atmos_src
  atmos_model.F90 atmos_tracer_driver.F90)

list(TRANSFORM atmos_src PREPEND src/)

add_library(atmos_cpl ${atmos_src})
target_link_libraries(atmos_cpl FMS::fms_r8)

set_target_properties(atmos_cpl PROPERTIES
  Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/include
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_BINARY_DIR}/include)
