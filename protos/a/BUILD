load("@rules_buf//buf:defs.bzl", "buf_lint_test")
load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "a_proto",
    srcs = ["a.proto"],
    visibility = ["//visibility:public"],
)

proto_library(
    name = "a1_proto",
    srcs = ["a1.proto"],
    visibility = ["//visibility:public"],
)

buf_lint_test(
    name = "a_proto_lint",
    config = "//:buf.yaml",
    targets = [":a_proto"],
)

buf_lint_test(
    name = "a1_proto_lint",
    config = "//:buf.yaml",
    targets = [":a1_proto"],
)
