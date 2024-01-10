load("@io_bazel_rules_go//go:def.bzl", "go_library", "go_test")

# Copyright 2015 Google Inc. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

go_library(
    name = "kindex",
    srcs = ["kindex.go"],
    importpath = "github.com/google/shipshape/third_party/kythe/go/platform/kindex",
    deps = [
        "//third_party/kythe/go/platform/analysis",
        "//third_party/kythe/go/platform/delimited",
        "//third_party/kythe/proto:analysis_go_proto",
        "@com_github_golang_protobuf//proto:go_default_library",
    ],
)

go_test(
    name = "kindex_test",
    srcs = ["kindex_test.go"],
    embed = [":kindex"],
    deps = [
        "//third_party/kythe/proto:analysis_go_proto",
        "//third_party/kythe/proto:storage_go_proto",
        "@com_github_golang_protobuf//proto:go_default_library",
    ],
)
