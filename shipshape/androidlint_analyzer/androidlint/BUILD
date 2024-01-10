load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_library", "go_test")

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

package(default_visibility = ["//shipshape:default_visibility"])

go_library(
    name = "androidlint",
    srcs = ["analyzer.go"],
    importpath = "github.com/google/shipshape/shipshape/androidlint_analyzer/androidlint",
    deps = [
        "//shipshape/proto:note_go_proto",
        "//shipshape/proto:shipshape_context_go_proto",
        "//shipshape/proto:textrange_go_proto",
        "@com_github_golang_protobuf//proto:go_default_library",
    ],
)

go_binary(
    name = "android_lint_service",
    srcs = ["service.go"],
    deps = [
        ":androidlint",
        "//shipshape/api",
        "//shipshape/proto:shipshape_context_proto_go",
        "//shipshape/util/rpc/server",
        "//third_party/go:protobuf",
    ],
)

go_test(
    name = "androidlint_test",
    srcs = ["analyzer_test.go"],
    data = glob(["testdata/**/*"]) + [
        # This is created by the configure script. It is a symlink to the
        # Android Lint binary installed on the system.
        ":lint",
    ],
    embed = [":androidlint"],
    deps = [
        "//shipshape/util/test",
    ],
)
