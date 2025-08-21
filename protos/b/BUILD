load("@rules_buf//buf:defs.bzl", "buf_lint_test")
load("@rules_proto//proto:defs.bzl", "proto_library")

proto_library(
    name = "b_proto",
    srcs = glob(["*.proto"]),
    visibility = ["//visibility:public"],
)

buf_lint_test(
    name = "b_proto_lint",
    config = "//:buf.yaml",
    targets = [":b_proto"],
)
