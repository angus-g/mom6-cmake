set(bergs_src
  icebergs.F90 icebergs_framework.F90 icebergs_io.F90)

list(TRANSFORM bergs_src PREPEND src/)

add_library(bergs_cpl ${bergs_src})
target_link_libraries(bergs_cpl FMS::fms_r8)

set_target_properties(bergs_cpl PROPERTIES
  Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/include
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_BINARY_DIR}/include)
