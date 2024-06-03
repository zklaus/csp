  kafka_header_files = ['KafkaAdapterManager.h', 'KafkaConsumer.h', 'KafkaInputAdapter.h', 'KafkaOutputAdapter.h', 'KafkaPublisher.h', 'KafkaSubscriber.h']
  kafka_source_files = ['KafkaAdapterManager.cpp', 'KafkaConsumer.cpp', 'KafkaInputAdapter.cpp', 'KafkaOutputAdapter.cpp', 'KafkaPublisher.cpp', 'KafkaSubscriber.cpp', kafka_header_files]
  csp_kafka_adapter_lib = static_library('csp_kafka_adapter', kafka_source_files)
  # set_target_properties(['csp_kafka_adapter', 'PROPERTIES', 'PUBLIC_HEADER', '${KAFKA_HEADER_FILES}'])
  DepsKafkaAdapter_dep = dependency('DepsKafkaAdapter')
  # target_link_libraries(['csp_kafka_adapter', 'PRIVATE', 'csp_adapter_utils', 'RdKafka::rdkafka', 'RdKafka::rdkafka++'])
  # install(['TARGETS', 'csp_kafka_adapter', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/adapters/kafka', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
