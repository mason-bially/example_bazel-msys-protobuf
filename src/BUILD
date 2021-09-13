package(default_visibility = ["//visibility:public"])

load("@rules_cc//cc:defs.bzl", "cc_test")
load("@rules_proto//proto:defs.bzl", "proto_library")
load("@rules_proto_grpc//cpp:defs.bzl", "cpp_proto_compile")
load("@rules_proto_grpc//cpp:defs.bzl", "cpp_grpc_compile")

proto_library(
    name = "pb_common",
    srcs = [":common.proto"],
)

proto_library(
    name = "pb_greeter",
    srcs = [":greeter.proto"],
    deps = [":pb_common"],
)

cpp_proto_compile(
    name = "pb_cpp_common",
    protos = [":pb_common"],
)

cpp_grpc_compile(
    name = "pb_cpp_greeter",
    protos = [":pb_greeter"],
    deps = [":pb_cpp_common"],
)

cc_test(
    name = "test",
    size = "small",
    srcs = ["greeter_client_test.cc"],
    deps = [
        "@gtest//:gtest",
        ":clientlib",
    ]
)

cc_binary(
    name = "client",
    srcs = ["greeter_client_main.cc"],
    deps = [":clientlib"],
)

cc_binary(
    name = "server",
    srcs = ["greeter_server.cc"],
    deps = [":pb_cpp_greeter"],
)

cc_library(
    name = "clientlib",
    srcs = ["greeter_client.cc"],
    hdrs = ["greeter_client.h"],
    deps = [":pb_cpp_greeter"],
)
