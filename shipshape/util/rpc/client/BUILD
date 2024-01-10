load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_library")

package(default_visibility = ["//visibility:public"])

go_library(
    name = "client",
    srcs = ["client.go"],
    importpath = "github.com/google/shipshape/shipshape/util/rpc/client",
    deps = [
        "//shipshape/util/httpencoding",
        "//shipshape/util/rpc/protocol",
    ],
)

go_binary(
    name = "example",
    srcs = ["example.go"],
    deps = [
        ":client",
    ],
)
