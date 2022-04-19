add_library(land_cpl src/land_model.F90)
target_link_libraries(land_cpl FMS::fms_r8)

set_target_properties(land_cpl PROPERTIES
  Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/include
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_BINARY_DIR}/include)
