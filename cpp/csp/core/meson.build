project(
  'csp_core',
  'cpp',
  version: '0.0.4',
  license: 'BSD-3',
  meson_version: '>= 1.1.0',
  default_options: [
    'cpp_std=c++17',
    'default_library=static',
  ],
)

PROJECT_VERSION = meson.project_version().split('.')
conf_data = configuration_data()
conf_data.set('CSP_VERSION_MAJOR', PROJECT_VERSION[0])
conf_data.set('CSP_VERSION_MINOR', PROJECT_VERSION[1])
conf_data.set('CSP_VERSION_PATCH', PROJECT_VERSION[2])
configure_file(input : 'Config.h.in',
               output : 'Config.h',
               configuration : conf_data)

core_public_headers = [
    'BasicAllocator.h',
    meson.current_build_dir()/'Config.h',
    'DynamicBitSet.h',
    'Enum.h',
    'EnumBitSet.h',
    'Exception.h',
    'FileUtils.h',
    'Generator.h',
    'Hash.h',
    'Likely.h',
    'QueueWaiter.h',
    'Platform.h',
    'SRMWLockFreeQueue.h',
    'System.h',
    'TaggedPointerUnion.h',
    'Time.h'
]

core_source_files = [
    core_public_headers,
    'Exception.cpp',
    'Time.cpp'
]

csp_core_lib = library(
    'csp_core',
    core_source_files,
    include_directories: '../../',
    install: true,
)

install_headers(core_public_headers, subdir: 'csp/core')
