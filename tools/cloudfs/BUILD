load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_library")

package(default_visibility = ["//shipshape:default_visibility"])

go_binary(
    name = "copy_cloud_repo",
    embed = [":cloudfs_lib"],
)

go_library(
    name = "cloudfs_lib",
    srcs = ["copy_cloud_repo.go"],
    importpath = "github.com/google/shipshape/tools/cloudfs",
    deps = ["//shipshape/util/file"],
)
