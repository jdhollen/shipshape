load("@rules_proto//proto:defs.bzl", "proto_library")
load("@io_bazel_rules_go//go:def.bzl", "go_library", "go_test")
load("@io_bazel_rules_go//proto:def.bzl", "go_proto_library")

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

proto_library(
    name = "test_proto",
    srcs = ["test.proto"],
)

go_proto_library(
    name = "test_go_proto",
    proto = ":test_proto",
)

go_library(
    name = "server",
    srcs = [
        "endpoint.go",
        "service.go",
    ],
    importpath = "github.com/google/shipshape/shipshape/util/rpc/server",
    deps = [
        "//shipshape/util/httpencoding",
        "//shipshape/util/rpc/protocol",
    ],
)

go_test(
    name = "server_test",
    srcs = ["krpc_test.go"],
    embed = [":server"],
    deps = [
        "@com_github_google_shipshape//shipshape/util/rpc/server:test_go_proto",
    ],
)
