load("@io_bazel_rules_go//go:def.bzl", "go_library")

go_library(
    name = "testdata",
    srcs = [
        "has_errors.go",
        "no_errors.go",
    ],
    importpath = "github.com/google/shipshape/shipshape/analyzers/govet/testdata",
    visibility = ["//visibility:public"],
)

exports_files(
    [
        "has_errors.go",
        "no_errors.go",
    ],
    visibility = ["//visibility:public"],
)
