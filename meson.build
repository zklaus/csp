###################################################################################################################################################
# Project Configuration #
#########################
project('csp', 'version', '0.0.4', default_options : ['default_library=static'])
cmake_cxx_standard = '20'
###################################################################################################################################################
# CMake Dependencies #
######################
###################################################################################################################################################
# CMake Policies #
##################
# option() should use new make behavior wrt variable clobbering
# cmake_policy(['SET', 'CMP0077', 'NEW'])
# Allow dep roots from env vars
# cmake_policy(['SET', 'CMP0074', 'NEW'])
# Set CMP0094 to NEW - find the first version that matches constraints,
# instead of the latest version installed
# cmake_policy(['SET', 'CMP0094', 'NEW'])
###################################################################################################################################################
# Environment #
###############
if cmake_system_name, 'MATCHES', 'Windows'
  win32 = 'ON'
  macos = 'OFF'
  linux = 'OFF'
elif cmake_system_name, 'MATCHES', 'Darwin'
  win32 = 'OFF'
  macos = 'ON'
  linux = 'OFF'
else
  win32 = 'OFF'
  macos = 'OFF'
  linux = 'ON'
endif
###################################################################################################################################################
# Paths #
#########
# Custom CMake modules
if 'NOT', 'DEFINED', 'CSP_CMAKE_MODULE_PATH'
  csp_cmake_module_path = '${CMAKE_SOURCE_DIR}/cpp/cmake/modules'
endif
# list(['PREPEND', 'CMAKE_MODULE_PATH', '${CSP_CMAKE_MODULE_PATH}'])
###################################################################################################################################################
# Build Configuration #
#######################
Color_dep = dependency('Color')
# Build options
# Extension options
# Normalize build type for downstream comparisons
# string(['TOLOWER', '${CMAKE_BUILD_TYPE}', 'CMAKE_BUILD_TYPE_LOWER'])
# Python library config
build_shared_libs = 'TRUE'
cmake_macosx_rpath = 'TRUE'
cmake_skip_rpath = 'FALSE'
cmake_skip_build_rpath = 'FALSE'
cmake_build_with_install_rpath = 'TRUE'
cmake_install_rpath_use_link_path = 'TRUE'
cmake_install_name_dir = '@rpath'
cmake_position_independent_code = 'ON'
# Normalize flags
# string(['REGEX', 'REPLACE', '[ ]*-O[^ ]+[ ]*', ' ', 'CMAKE_CXX_FLAGS', '${CMAKE_CXX_FLAGS}'])
# string(['REGEX', 'REPLACE', '[ ]*-Wl,-O2 -Wl,[^ ]+[ ]*', ' ', 'CMAKE_EXE_LINKER_FLAGS', '${CMAKE_EXE_LINKER_FLAGS}'])
# string(['REGEX', 'REPLACE', '[ ]*-Wl,-O2 -Wl,[^ ]+[ ]*', ' ', 'CMAKE_SHARED_LINKER_FLAGS', '${CMAKE_SHARED_LINKER_FLAGS}'])
# CCache setup
if 'CSP_USE_CCACHE'
  cmake_c_compile_launcher = 'ccache'
  cmake_cxx_compiler_launcher = 'ccache'
endif
if 'NOT', 'DEFINED', 'CSP_PYTHON_VERSION'
  csp_python_version = '3.12'
endif
# Path to python folder for autogen
if 'NOT', 'DEFINED', 'CSP_PYTHON_FOLDER'
  csp_python_folder = [cmake_source_dir, '/csp']
  # get_filename_component(['CSP_PYTHON_FOLDER', csp_python_folder, 'REALPATH', 'BASE_DIR', cmake_binary_dir])
endif
if 'MACOS'
  # fix for threads on osx
  # assume built-in pthreads on MacOS
  cmake_thread_libs_init = '-lpthread'
  cmake_have_threads_library = '1'
  cmake_use_win32_threads_init = '0'
  cmake_use_pthreads_init = '1'
  threads_prefer_pthread_flag = 'ON'
  # don't link against build python
  # https://blog.tim-smith.us/2015/09/python-extension-modules-os-x/
  cmake_shared_linker_flags = '${CMAKE_SHARED_LINKER_FLAGS} -undefined dynamic_lookup'
endif
###################################################################################################################################################
# Version Information #
#######################
# Set version from cmake and extract latest hash if available
csp_version_major = project_version_major
csp_version_minor = project_version_minor
csp_version_patch = project_version_patch
if 'EXISTS', '${CMAKE_CURRENT_SOURCE_DIR}/.git'
  # Get latest commit
  # execute_process(['COMMAND', 'git', 'rev-parse', 'HEAD', 'WORKING_DIRECTORY', cmake_current_source_dir, 'OUTPUT_VARIABLE', 'CSP_VERSION_COMMIT_SHA'])
  # strip newline
  # string(['REGEX', 'REPLACE', '\n$', '', 'CSP_VERSION_COMMIT_SHA', '${CSP_VERSION_COMMIT_SHA}'])
else
  csp_version_commit_sha = 'release'
endif
###################################################################################################################################################
# RPath #
#########
if 'MACOS'
  cmake_install_rpath = '@loader_path/'
elif 'LINUX'
  cmake_install_rpath = '\$ORIGIN'
endif
###################################################################################################################################################
# Flags #
# Optimization Flags
if 'WIN32'
  if 'CMAKE_BUILD_TYPE_LOWER', 'STREQUAL', 'debug'
    cmake_cxx_flags = '${CMAKE_CXX_FLAGS} /DEBUG /Z7 /Zi'
    # add_definitions('-DCSP_DEBUG')
  else
    cmake_cxx_flags = '${CMAKE_CXX_FLAGS} /O2'
    # add_definitions('-DNDEBUG')
  endif
  cmake_cxx_flags = '${CMAKE_CXX_FLAGS} /EHsc /MP /bigobj'
  # foreach(['warning', '4244', '4251', '4267', '4275', '4290', '4786', '4305', '4996'])
  cmake_cxx_flags = '${CMAKE_CXX_FLAGS} /wd${warning}'
  # endforeach('warning')
  # add_compile_definitions(['WIN32', '_WIN32'])
else
  if 'CSP_BUILD_NO_CXX_ABI'
    cmake_cxx_flags = '${CMAKE_CXX_FLAGS} -D_GLIBCXX_USE_CXX11_ABI=0'
  endif
  if 'COVERAGE'
    # TODO windows
    # add_compile_options('--coverage')
    cmake_cxx_flags = '-O0 ${CMAKE_CXX_FLAGS}'
    # link_libraries('gcov')
  endif
  if 'GPROF_BUILD'
    cmake_cxx_flags = '-pg ${CMAKE_CXX_FLAGS}'
    cmake_exe_linker_flags = '-pg ${CMAKE_EXE_LINKER_FLAGS}'
    cmake_shared_linker_flags = '-pg ${CMAKE_SHARED_LINKER_FLAGS}'
  endif
  if 'CMAKE_BUILD_TYPE_LOWER', 'STREQUAL', 'debug'
    cmake_cxx_flags = '${CMAKE_CXX_FLAGS} -O0 -g3'
    # add_definitions('-DCSP_DEBUG')
  else
    cmake_cxx_flags = '${CMAKE_CXX_FLAGS} -O3 -g0 -Wall -Wno-deprecated-declarations -Wno-deprecated'
    # add_definitions('-DNDEBUG')
    if 'CMAKE_CXX_COMPILER_ID', 'STREQUAL', 'GNU'
      cmake_cxx_flags = '${CMAKE_CXX_FLAGS} -Wno-maybe-uninitialized'
    endif
  endif
endif
###################################################################################################################################################
# Messages #
############
# message('\n${Green}Building CSP version v${CSP_VERSION_MAJOR}.${CSP_VERSION_MINOR}.${CSP_VERSION_PATCH} [${CSP_VERSION_COMMIT_SHA}]')
# message('\n${Green}Building C++ binding${ColorReset}')
# message('\n${Green}Building Python ${Red}${CSP_PYTHON_VERSION}${Green} binding${ColorReset}')
if 'CMAKE_BUILD_TYPE_LOWER', 'STREQUAL', 'debug'
  # message('\n${Red}Building DEBUG${ColorReset}')
else
  # message('\n${Green}Building RELEASE${ColorReset}')
endif
# message('\n${Green}CMake Search Path: ${CMAKE_MODULE_PATH}${ColorReset}')
###################################################################################################################################################
# Helpers #
###########
# FIXME: consolidate this function with Findcsp_autogen.cmake
# function(['csp_autogen', 'MODULE_NAME', 'DEST_FILENAME', 'HEADER_NAME_OUTVAR', 'SOURCE_NAME_OUTVAR'])
# string(['REPLACE', '.', '\/', 'MODULE_FILENAME', module_name])
# string(['JOIN', '.', 'MODULE_FILENAME', module_filename, 'py'])
# add_custom_target(['mkdir_autogen_${MODULE_NAME}', 'ALL', 'COMMAND', cmake_command, '-E', 'make_directory', '${CMAKE_CURRENT_BINARY_DIR}/csp_autogen'])
# VARARGS done by position
if 'ARGV4'
  csp_autogen_extra_args = '${ARGV4}'
else
  csp_autogen_extra_args = ''
endif
# cmake_path(['SET', 'CSP_AUTOGEN_MODULE_PATH', 'NORMALIZE', '${CMAKE_SOURCE_DIR}/csp/build/csp_autogen.py'])
# cmake_path(['SET', 'CSP_AUTOGEN_DESTINATION_FOLDER', 'NORMALIZE', '${CMAKE_CURRENT_BINARY_DIR}/csp_autogen'])
# cmake_path(['SET', 'CSP_AUTOTGEN_CPP_OUT', 'NORMALIZE', '${CMAKE_CURRENT_BINARY_DIR}/csp_autogen/${DEST_FILENAME}.cpp'])
# cmake_path(['SET', 'CSP_AUTOTGEN_H_OUT', 'NORMALIZE', '${CMAKE_CURRENT_BINARY_DIR}/csp_autogen/${DEST_FILENAME}.h'])
# if(${CMAKE_SYSTEM_NAME} MATCHES "Windows")
#     set(CSP_AUTOGEN_PYTHONPATH ${PROJECT_BINARY_DIR}/lib/${CMAKE_BUILD_TYPE};${CMAKE_SOURCE_DIR};%PYTHONPATH% )
# else()
#     set(CSP_AUTOGEN_PYTHONPATH ${PROJECT_BINARY_DIR}/lib:${CMAKE_SOURCE_DIR}:$$PYTHONPATH )
# endif()
# add_custom_command(['OUTPUT', '${CSP_AUTOTGEN_CPP_OUT}', '${CSP_AUTOTGEN_H_OUT}', 'COMMAND', cmake_command, '-E', 'env', 'PYTHONPATH=${CSP_AUTOGEN_PYTHONPATH}', python_executable, csp_autogen_module_path, '-m', module_name, '-d', csp_autogen_destination_folder, '-o', dest_filename, csp_autogen_extra_args, 'COMMENT', 'generating csp c++ types from module ${MODULE_NAME}', 'DEPENDS', 'mkdir_autogen_${MODULE_NAME}', cmake_source_dir, '/csp/build/csp_autogen.py', cmake_source_dir, '/${MODULE_FILENAME}', 'csptypesimpl'])
source_name_outvar = ['${CMAKE_CURRENT_BINARY_DIR}/csp_autogen/${DEST_FILENAME}.cpp', 'PARENT_SCOPE']
header_name_outvar = ['${CMAKE_CURRENT_BINARY_DIR}/csp_autogen/${DEST_FILENAME}.h', 'PARENT_SCOPE']
# endfunction()
###################################################################################################################################################
# Dependencies #
################
DepsBase_dep = dependency('DepsBase')
# Adapter dependencies
if 'CSP_BUILD_KAFKA_ADAPTER'
  DepsKafkaAdapter_dep = dependency('DepsKafkaAdapter')
endif
if 'CSP_BUILD_PARQUET_ADAPTER'
  DepsParquetAdapter_dep = dependency('DepsParquetAdapter')
endif
# PYTHON
if 'CSP_MANYLINUX'
  # Manylinux docker images have no shared libraries
  # The instead use a statically built python.
  # Cmake's default FindPython can't find the python headers
  # without also finding (or failing to find) the python libraries
  # so we use a custom FindPythonHeaders that is the same as the
  # default, but ignores when the python libraries can't be found.
  # message('${Red}Manylinux build has no python shared libraries${ColorReset}')
  Python_dep = dependency('Python')
  PythonHeaders_dep = dependency('PythonHeaders')
  # Run with exact version so its cached for pybind
  PythonInterp_dep = dependency('PythonInterp')
else
  # message('${Cyan}Use python shared libraries${ColorReset}')
  Python_dep = dependency('Python')
  # Run with exact version so its cached for pybind
  PythonInterp_dep = dependency('PythonInterp')
  PythonLibs_dep = dependency('PythonLibs')
  # link_directories(python_library_dirs)
endif
# message('${Cyan}Using Python ${Python_VERSION}\nPython_INCLUDE_DIRS: ${Python_INCLUDE_DIRS}\nPython_LIBRARIES: ${Python_LIBRARIES}\nPython_EXECUTABLE: ${Python_EXECUTABLE} ${ColorReset}')
# include_directories(python_include_dirs)
# NUMPY
Numpy_dep = dependency('Numpy')
if 'NOT', 'NUMPY_FOUND'
  # message(['FATAL_ERROR', '${Red}Numpy could not be located${ColorReset}'])
else
  # message('${Cyan}Numpy found: ${NUMPY_INCLUDE_DIR}${ColorReset}')
  # include_directories(numpy_include_dir)
endif
#####################
###################################################################################################################################################
# Asset names #
################
# prefix is _ by default
cmake_shared_library_prefix = '_'
if 'NOT', 'WIN32'
  # shared suffix is .so for both linux and mac
  cmake_shared_library_suffix = '.so'
  # static suffix is _static.a # TODO decide if we want this
  cmake_static_library_suffix = '_static.a'
else
  # shared suffix is .pyd for windows
  cmake_shared_library_suffix = '.pyd'
endif
###################################################################################################################################################
# Build assets #
################
# include_directories('${CMAKE_SOURCE_DIR}/cpp')
# for autogen
# include_directories('${CMAKE_BINARY_DIR}/cpp')
cmake_archive_output_directory = [cmake_binary_dir, '/lib']
cmake_library_output_directory = [cmake_binary_dir, '/lib']
if 'WIN32'
  # On windows, force dlls into lib folder
  cmake_runtime_output_directory = [cmake_binary_dir, '/lib']
  csp_runtime_install_subdir = 'lib/'
else
  cmake_runtime_output_directory = [cmake_binary_dir, '/bin']
  csp_runtime_install_subdir = 'bin/'
endif
subdir('cpp/csp/adapters')
subdir('cpp/csp/core')
subdir('cpp/csp/cppnodes')
subdir('cpp/csp/engine')
subdir('cpp/csp/python')
subdir('cpp/csp/python/adapters')
###################################################################################################################################################
# Tests #
#########
if 'CSP_BUILD_TESTS'
  subdir('cpp/tests')
endif
