adapter_utils_public_headers = ['JSONMessageStructConverter.h', 'JSONMessageWriter.h', 'MessageEnums.h', 'MessageWriter.h', 'MessageStructConverter.h', 'ProtobufHelper.h', 'ProtobufMessageStructConverter.h', 'RawBytesMessageStructConverter.h', 'StructAdapterInfo.h', 'ValueDispatcher.h']
adapter_utils_files = ['JSONMessageStructConverter.cpp', 'MessageWriter.cpp', 'MessageEnums.cpp', 'MessageStructConverter.cpp', 'ProtobufHelper.cpp', 'ProtobufMessageStructConverter.cpp', 'RawBytesMessageStructConverter.cpp']
csp_adapter_utils_lib = static_library('csp_adapter_utils', adapter_utils_files)
# set_target_properties(['csp_adapter_utils', 'PROPERTIES', 'PUBLIC_HEADER', '${ADAPTER_UTILS_PUBLIC_HEADERS}'])
Protobuf_dep = dependency('Protobuf')
# target_link_libraries(['csp_adapter_utils', 'PRIVATE', 'protobuf::libprotoc', 'protobuf::libprotobuf', 'protobuf::libprotobuf-lite'])
# install(['TARGETS', 'csp_adapter_utils', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/adapters/utils', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
