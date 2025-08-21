load("@rules_buf//buf:defs.bzl", "buf_lint_test")
load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "c_proto",
    srcs = ["c.proto"],
    visibility = ["//visibility:public"],
)

buf_lint_test(
    name = "c_proto_lint",
    config = "//:buf.yaml",
    targets = [":c_proto"],
)
