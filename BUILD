load(
    "@protobuf//:protobuf.bzl",
    "cc_proto_library",
)

cc_library(
    name = "protocol",
    srcs = ["protocol.cc"],
    hdrs = ["protocol.h"],
    deps = [
        "@boringssl//:crypto",
        "@protobuf//:protobuf",
    ],
)

cc_test(
    name = "protocol_test",
    srcs = ["protocol_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":protocol",
        "@gtest//:main",
    ],
)

cc_library(
    name = "client",
    srcs = ["client.cc"],
    hdrs = ["client.h"],
    deps = [":protocol"],
)

cc_test(
    name = "client_test",
    srcs = ["client_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":client",
        ":open_source_fillins",
        "@gtest//:main",
    ],
)

cc_library(
    name = "time_source",
    hdrs = ["time_source.h"],
    deps = [":protocol"],
)

cc_library(
    name = "server",
    srcs = ["server.cc"],
    hdrs = ["server.h"],
    deps = [
        ":protocol",
        ":time_source",
        "@boringssl//:crypto",
    ],
)

cc_proto_library(
    name = "config_proto",
    srcs = ["config.proto"],
    default_runtime = "@protobuf//:protobuf",
    protoc = "@protobuf//:protoc",
)

cc_binary(
    name = "simple_client",
    srcs = [
        "clock_linux.cc",
        "clock_macos.cc",
        "simple_client.cc",
    ],
    deps = [
        ":client",
        ":config_proto",
        "@boringssl//:crypto",
        "@protobuf//:protobuf",
    ],
)

cc_library(
    name = "simple_server_lib",
    srcs = ["simple_server.cc"],
    hdrs = ["simple_server.h"],
    deps = [
        ":server",
        ":sys_time",
        ":udp_processor",
    ],
)

cc_binary(
    name = "simple_server",
    srcs = ["simple_server_main.cc"],
    deps = [":simple_server_lib"],
)

cc_library(
    name = "open_source_fillins",
    hdrs = ["open_source_fillins.h"],
    defines = ["ROUGHTIME_OPEN_SOURCE"],
)

cc_test(
    name = "server_test",
    srcs = ["server_test.cc"],
    copts = ["-Iexternal/gtest/include"],
    deps = [
        ":open_source_fillins",
        ":server",
        "@boringssl//:crypto",
        "@gtest//:main",
    ],
)

cc_library(
    name = "udp_processor",
    srcs = ["udp_processor.cc"],
    hdrs = ["udp_processor.h"],
    deps = [
        ":open_source_fillins",
        ":protocol",
        ":server",
        ":time_source",
    ],
)

cc_library(
    name = "sys_time",
    srcs = ["sys_time.cc"],
    hdrs = ["sys_time.h"],
    deps = [
        ":time_source",
        "@protobuf//:protobuf",
    ],
)
