ADD_LIBRARY(solver_pcg ${G2O_LIB_TYPE}
  solver_pcg.cpp
  linear_solver_pcg.h  
  linear_solver_pcg.hpp
)

SET_TARGET_PROPERTIES(solver_pcg PROPERTIES OUTPUT_NAME ${LIB_PREFIX}solver_pcg)

TARGET_LINK_LIBRARIES(solver_pcg core)
if(PROFILER_LIB)
target_link_libraries(PROFILER_LIB)
endif()

INSTALL(TARGETS solver_pcg
  RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
  LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
  ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)

FILE(GLOB headers "${CMAKE_CURRENT_SOURCE_DIR}/*.h" "${CMAKE_CURRENT_SOURCE_DIR}/*.hpp")

INSTALL(FILES ${headers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/g2o/solvers/pcg)
