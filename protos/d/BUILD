load("@rules_buf//buf:defs.bzl", "buf_lint_test")
load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "d_proto",
    srcs = ["d.proto"],
    visibility = ["//visibility:public"],
)

buf_lint_test(
    name = "d_proto_lint",
    config = "//:buf.yaml",
    targets = [":d_proto"],
)
