  parquet_header_files = ['ArrowIPCFileReaderWrapper.h', 'ArrowIPCFileWriterWrapper.h', 'ArrowSingleColumnArrayBuilder.h', 'DialectGenericListReaderInterface.h', 'DialectGenericListWriterInterface.h', 'FileReaderWrapper.h', 'FileWriterWrapper.h', 'ParquetFileWriterWrapper.h', 'ParquetFileReaderWrapper.h', 'FileWriterWrapperContainer.h', 'ParquetDictBasketOutputWriter.h', 'ParquetInputAdapterManager.h', 'ParquetOutputAdapter.h', 'ParquetOutputAdapterManager.h', 'ParquetOutputFilenameAdapter.h', 'ParquetReader.h', 'ParquetReaderColumnAdapter.h', 'ParquetStatusUtils.h', 'ParquetWriter.h']
  parquet_source_files = ['ArrowIPCFileReaderWrapper.cpp', 'ArrowIPCFileWriterWrapper.cpp', 'FileReaderWrapper.cpp', 'FileWriterWrapper.cpp', 'ParquetFileWriterWrapper.cpp', 'ParquetFileReaderWrapper.cpp', 'FileWriterWrapperContainer.cpp', 'ParquetDictBasketOutputWriter.cpp', 'ParquetInputAdapterManager.cpp', 'ParquetOutputAdapter.cpp', 'ParquetOutputAdapterManager.cpp', 'ParquetOutputFilenameAdapter.cpp', 'ParquetReader.cpp', 'ParquetReaderColumnAdapter.cpp', 'ParquetWriter.cpp', parquet_header_files]
  csp_parquet_adapter_lib = static_library('csp_parquet_adapter', parquet_source_files)
  # set_target_properties(['csp_parquet_adapter', 'PROPERTIES', 'PUBLIC_HEADER', '${PARQUET_HEADER_FILES}'])
  # target_include_directories(['csp_parquet_adapter', 'PRIVATE', arrow_include_dir, parquet_include_dir])
  Arrow_dep = dependency('Arrow')
  Parquet_dep = dependency('Parquet')
  Thrift_dep = dependency('Thrift')
  lz4_dep = dependency('lz4')
  utf8proc_dep = dependency('utf8proc')
  Brotli_dep = dependency('Brotli')
  if 'WIN32'
    if 'CSP_USE_VCPKG'
      arrow_packages_to_link = ['Arrow::arrow_static', 'Parquet::parquet_static']
      # target_compile_definitions(['csp_parquet_adapter', 'PUBLIC', 'ARROW_STATIC'])
      # target_compile_definitions(['csp_parquet_adapter', 'PUBLIC', 'PARQUET_STATIC'])
    else
      # use dynamic variants
      # Until we manage to get the fix for ws3_32.dll in arrow-16 into conda, manually fix the error here
      # get_target_property(['LINK_LIBS', 'Arrow::arrow_shared', 'INTERFACE_LINK_LIBRARIES'])
      # string(['REPLACE', 'ws2_32.dll', 'ws2_32', 'FIXED_LINK_LIBS', '${LINK_LIBS}'])
      # set_target_properties(['Arrow::arrow_shared', 'PROPERTIES', 'INTERFACE_LINK_LIBRARIES', '${FIXED_LINK_LIBS}'])
      arrow_packages_to_link = ['parquet_shared', 'arrow_shared']
    endif
  else
    if 'CSP_USE_VCPKG'
      # use static variants
      arrow_packages_to_link = ['parquet_static', 'arrow_static']
    else
      # use dynamic variants
      arrow_packages_to_link = ['parquet', 'arrow']
    endif
  endif
  # target_link_libraries(['csp_parquet_adapter', 'PRIVATE', 'csp_adapter_utils', 'thrift::thrift', 'lz4::lz4', 'utf8proc::utf8proc', brotli_static_lib, arrow_packages_to_link])
  # install(['TARGETS', 'csp_parquet_adapter', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/adapters/parquet', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
