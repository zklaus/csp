core_public_headers = ['BasicAllocator.h', 'Config.h.in', 'DynamicBitSet.h', 'Enum.h', 'EnumBitSet.h', 'Exception.h', 'FileUtils.h', 'Generator.h', 'Hash.h', 'Likely.h', 'QueueWaiter.h', 'Platform.h', 'SRMWLockFreeQueue.h', 'System.h', 'TaggedPointerUnion.h', 'Time.h']
core_source_files = ['Exception.cpp', 'Time.cpp', core_public_headers]
# configure_file(['Config.h.in', cmake_current_binary_dir, '/cpp/csp/core/Config.h'])
csp_core_lib = static_library('csp_core', core_source_files)
# set_target_properties(['csp_core', 'PROPERTIES', 'PUBLIC_HEADER', '${CORE_PUBLIC_HEADERS}'])
# install(['TARGETS', 'csp_core', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/core', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
# install(['FILES', cmake_current_binary_dir, '/cpp/csp/core/Config.h', 'DESTINATION', 'include/csp/core'])
