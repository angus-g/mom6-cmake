set(SIS_src
  config_src/external/Icepack_interfaces/icepack_itd.F90 config_src/external/Icepack_interfaces/icepack_kinds.F90 config_src/external/Icepack_interfaces/icepack_mechred.F90 config_src/external/Icepack_interfaces/icepack_parameters.F90 config_src/external/Icepack_interfaces/icepack_tracers.F90 config_src/external/Icepack_interfaces/icepack_warnings.F90
  src/SIS2_ice_thm.F90
  src/SIS_continuity.F90 src/SIS_ctrl_types.F90 src/SIS_debugging.F90 src/SIS_diag_mediator.F90 src/SIS_dyn_bgrid.F90 src/SIS_dyn_cgrid.F90 src/SIS_dyn_trans.F90 src/SIS_fast_thermo.F90 src/SIS_fixed_initialization.F90 src/SIS_framework.F90 src/SIS_get_input.F90 src/SIS_hor_grid.F90 src/SIS_ice_diags.F90 src/SIS_optics.F90 src/SIS_restart.F90 src/SIS_slow_thermo.F90 src/SIS_state_initialization.F90 src/SIS_sum_output.F90 src/SIS_tracer_advect.F90 src/SIS_tracer_flow_control.F90 src/SIS_tracer_registry.F90 src/SIS_transcribe_grid.F90 src/SIS_transport.F90 src/SIS_types.F90 src/SIS_utils.F90
  src/combined_ice_ocean_driver.F90
  src/ice_age_tracer.F90 src/ice_boundary_types.F90 src/ice_grid.F90 src/ice_model.F90 src/ice_ridge.F90 src/ice_shortwave_dEdd.F90 src/ice_spec.F90 src/ice_thm.F90 src/ice_type.F90
  src/slab_ice.F90 src/specified_ice.F90)

set(SIS_inc
  config_src/${MOM_memory} src)

list(TRANSFORM SIS_src PREPEND src/)
list(TRANSFORM SIS_inc PREPEND src/)

add_library(SIS2_cpl ${SIS_src})
target_include_directories(SIS2_cpl PRIVATE
  ${SIS_inc} ../MOM6/src/src/framework)
target_link_libraries(SIS2_cpl MOM6_cpl bergs_cpl iceparam_cpl FMS::fms_r8)

set_target_properties(SIS2_cpl PROPERTIES
  Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/include
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_BINARY_DIR}/include)

