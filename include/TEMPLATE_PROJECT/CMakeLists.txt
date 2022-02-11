message(STATUS "TODO: Replace TEMPLATE_PROJECT with the real project name in include/TEMPLATE_PROJECT/CMakeLists.txt")

# Project header files
list(
  APPEND
  TEMPLATE_PROJECT_HEADERS

)

# Add configure_file commands here if necessary

install(FILES
${TEMPLATE_PROJECT_HEADERS}
DESTINATION ${TEMPLATE_PROJECT_INCLUDE_DIR})