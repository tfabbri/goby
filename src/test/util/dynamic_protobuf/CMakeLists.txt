protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS test_a.proto)
add_executable(goby_test_dynamic_protobuf dynamic_protobuf.cpp ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(goby_test_dynamic_protobuf goby_util goby_common ${Boost_LIBRARIES} ${PROTOBUF_LIBRARIES} ${CMAKE_DL_LIBS})
add_test(goby_test_dynamic_protobuf ${goby_BIN_DIR}/goby_test_dynamic_protobuf)


protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS test_b.proto)
add_library(test_dyn_protobuf SHARED ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(test_dyn_protobuf dl ${PROTOBUF_LIBRARIES})
