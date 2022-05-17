project(devtools-deepin)

## Setup
cmake_minimum_required(VERSION 2.8)
set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH}"
  "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

include(GNUInstallDirs)

function(install_build_script cmd)
  add_custom_command(OUTPUT "${CMAKE_CURRENT_BINARY_DIR}/cmds/${cmd}"
    COMMAND "${CMAKE_COMMAND}" -E make_directory
    "${CMAKE_CURRENT_BINARY_DIR}/cmds"
    COMMAND "${CMAKE_COMMAND}" -E create_symlink archbuild
    "${CMAKE_CURRENT_BINARY_DIR}/cmds/${cmd}")
  add_custom_target(${cmd}.target ALL
    DEPENDS "${CMAKE_CURRENT_BINARY_DIR}/cmds/${cmd}")
endfunction()

install_build_script(deepin-x86_64-build)

install(DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/cmds/"
  DESTINATION "${CMAKE_INSTALL_BINDIR}")
install(FILES
  "pacman-deepin.conf"
  DESTINATION "${CMAKE_INSTALL_DATAROOTDIR}/devtools/")
