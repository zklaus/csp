project(
  'csp_core',
  'cpp',
  version: '1.15.0.dev0',
  license: 'BSD-3',
  meson_version: '>= 1.1.0',
  default_options: [
    'c_std=c17',
    'cpp_std=c++17',
  ],
)

conf_data = configuration_data()
py3 = import('python').find_installation(pure: false)
PROJECT_VERSION_MAJOR = run_command(py3, '-c', 'import os; print(os.environ["PROJECT_VERSION_MAJOR"])')
PROJECT_VERSION_MINOR = run_command(py3, '-c', 'import os; print(os.environ["PROJECT_VERSION_MINOR"])')
PROJECT_VERSION_PATCH = run_command(py3, '-c', 'import os; print(os.environ["PROJECT_VERSION_PATCH"])')
conf_data.set('CSP_VERSION_MAJOR', PROJECT_VERSION_MAJOR.stdout().strip())
conf_data.set('CSP_VERSION_MINOR', PROJECT_VERSION_MINOR.stdout().strip())
conf_data.set('CSP_VERSION_PATCH', PROJECT_VERSION_PATCH.stdout().strip())
configure_file(input : 'Config.h.in',
               output : 'Config.h',
               configuration : conf_data)

core_public_headers = ['BasicAllocator.h', meson.current_build_dir()/'Config.h', 'DynamicBitSet.h', 'Enum.h', 'EnumBitSet.h', 'Exception.h', 'FileUtils.h', 'Generator.h', 'Hash.h', 'Likely.h', 'QueueWaiter.h', 'Platform.h', 'SRMWLockFreeQueue.h', 'System.h', 'TaggedPointerUnion.h', 'Time1.h']
core_source_files = [core_public_headers, 'Exception.cpp', 'Time.cpp']
csp_core_lib = static_library(
    'csp_core',
    core_source_files
    )
