``` sh
> buf lint .
protos/a/a.proto:3:1:Multiple directories "protos/a,protos/c" contain files with package "protos.a".
protos/a/a.proto:5:1:Files in package "protos.a" have multiple values "github.com/purajit/test_rules_buf/protos/a,github.com/purajit/test_rules_buf/protos/a1,github.com/purajit/test_rules_buf/protos/c" for option "go_package" and all values must be equal.
protos/a/a1.proto:3:1:Multiple directories "protos/a,protos/c" contain files with package "protos.a".
protos/a/a1.proto:5:1:Files in package "protos.a" have multiple values "github.com/purajit/test_rules_buf/protos/a,github.com/purajit/test_rules_buf/protos/a1,github.com/purajit/test_rules_buf/protos/c" for option "go_package" and all values must be equal.
protos/b/b.proto:5:1:Files in package "protos.b" have multiple values "github.com/purajit/test_rules_buf/protos/b,github.com/purajit/test_rules_buf/protos/b1" for option "go_package" and all values must be equal.
protos/b/b1.proto:5:1:Files in package "protos.b" have multiple values "github.com/purajit/test_rules_buf/protos/b,github.com/purajit/test_rules_buf/protos/b1" for option "go_package" and all values must be equal.
protos/c/c.proto:3:1:Multiple directories "protos/a,protos/c" contain files with package "protos.a".
protos/c/c.proto:5:1:Files in package "protos.a" have multiple values "github.com/purajit/test_rules_buf/protos/a,github.com/purajit/test_rules_buf/protos/a1,github.com/purajit/test_rules_buf/protos/c" for option "go_package" and all values must be equal.

> protoc -I . --buf-lint_out=. $(find . -name '*.proto')
--buf-lint_out: protos/a/a.proto:3:1:Multiple directories "protos/a,protos/c" contain files with package "protos.a".
protos/a/a.proto:5:1:Files in package "protos.a" have multiple values "github.com/purajit/test_rules_buf/protos/a,github.com/purajit/test_rules_buf/protos/a1,github.com/purajit/test_rules_buf/protos/c" for option "go_package" and all values must be equal.
protos/a/a1.proto:3:1:Multiple directories "protos/a,protos/c" contain files with package "protos.a".
protos/a/a1.proto:5:1:Files in package "protos.a" have multiple values "github.com/purajit/test_rules_buf/protos/a,github.com/purajit/test_rules_buf/protos/a1,github.com/purajit/test_rules_buf/protos/c" for option "go_package" and all values must be equal.
protos/b/b.proto:5:1:Files in package "protos.b" have multiple values "github.com/purajit/test_rules_buf/protos/b,github.com/purajit/test_rules_buf/protos/b1" for option "go_package" and all values must be equal.
protos/b/b1.proto:5:1:Files in package "protos.b" have multiple values "github.com/purajit/test_rules_buf/protos/b,github.com/purajit/test_rules_buf/protos/b1" for option "go_package" and all values must be equal.
protos/c/c.proto:3:1:Multiple directories "protos/a,protos/c" contain files with package "protos.a".
protos/c/c.proto:5:1:Files in package "protos.a" have multiple values "github.com/purajit/test_rules_buf/protos/a,github.com/purajit/test_rules_buf/protos/a1,github.com/purajit/test_rules_buf/protos/c" for option "go_package" and all values must be equal.

> bazel test //...
INFO: Analyzed 10 targets (0 packages loaded, 0 targets configured).
FAIL: //protos/b:b_proto_lint (Exit 1) (see /private/var/tmp/_bazel_user/d8401fa639985ba14836083e2017b96c/execroot/_main/bazel-out/darwin_arm64-fastbuild/testlogs/protos/b/b_proto_lint/test.log)
INFO: From Testing //protos/b:b_proto_lint:
==================== Test output for //protos/b:b_proto_lint:
--buf-plugin_out: protos/b/b.proto:5:1:Files in package "protos.b" have multiple values "github.com/purajit/test_rules_buf/protos/b,github.com/purajit/test_rules_buf/protos/b1" for option "go_package" and all values must be equal.
protos/b/b1.proto:5:1:Files in package "protos.b" have multiple values "github.com/purajit/test_rules_buf/protos/b,github.com/purajit/test_rules_buf/protos/b1" for option "go_package" and all values must be equal.
================================================================================
INFO: Found 5 targets and 5 test targets...
INFO: Elapsed time: 0.255s, Critical Path: 0.14s
INFO: 2 processes: 4 action cache hit, 2 darwin-sandbox.
INFO: Build completed, 1 test FAILED, 2 total actions
//protos/a:a1_proto_lint                                        (cached) PASSED in 0.1s
//protos/a:a_proto_lint                                         (cached) PASSED in 0.3s
//protos/c:c_proto_lint                                         (cached) PASSED in 0.3s
//protos/d:d_proto_lint                                         (cached) PASSED in 0.3s
//protos/b:b_proto_lint                                                  FAILED in 0.1s
  /private/var/tmp/_bazel_user/d8401fa639985ba14836083e2017b96c/execroot/_main/bazel-out/darwin_arm64-fastbuild/testlogs/protos/b/b_proto_lint/test.log

Executed 1 out of 5 tests: 4 tests pass and 1 fails locally.

```
