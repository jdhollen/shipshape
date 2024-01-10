load("@bazel_gazelle//:def.bzl", "gazelle")

# gazelle:proto disable
# gazelle:build_file_name BUILD,BUILD.bazel
# gazelle:prefix github.com/google/shipshape
# gazelle:exclude **/node_modules/**
# gazelle:exclude shipshape/analyzers/govet/testdata
gazelle(name = "gazelle")
