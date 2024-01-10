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

go_binary(
    name = "go_dispatcher",
    srcs = ["go_dispatcher.go"],
    deps = [
        "//shipshape/analyzers/codealert",
        "//shipshape/analyzers/govet",
        "//shipshape/analyzers/jshint",
        "//shipshape/analyzers/postmessage",
        "//shipshape/analyzers/pylint",
        "//shipshape/analyzers/wordcount",
        "//shipshape/api",
        "//shipshape/proto:note_go_proto",
        "//shipshape/proto:shipshape_context_go_proto",
        "//shipshape/util/rpc/server",
    ],
)

go_library(
    name = "service",
    srcs = [
        "config.go",
        "driver.go",
    ],
    importpath = "github.com/google/shipshape/shipshape/service",
    deps = [
        "//shipshape/proto:note_go_proto",
        "//shipshape/proto:shipshape_config_go_proto",
        "//shipshape/proto:shipshape_context_go_proto",
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/util/defaults",
        "//shipshape/util/file",
        "//shipshape/util/rpc/client",
        "//shipshape/util/rpc/server",
        "//shipshape/util/strings",
        "@com_github_golang_protobuf//proto:go_default_library",
        "@in_gopkg_yaml_v2//:yaml_v2",
    ],
)

go_binary(
    name = "shipshape",
    srcs = ["shipshape.go"],
    deps = [
        ":service",
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/util/rpc/server",
        "//shipshape/util/strings",
    ],
)

go_test(
    name = "service_test",
    srcs = [
        "config_test.go",
        "driver_test.go",
    ],
    data = glob(["testdata/service_test/**/*"]),
    embed = [":service"],
    deps = [
        "//shipshape/proto:note_go_proto",
        "//shipshape/proto:shipshape_context_go_proto",
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/util/rpc/server",
        "//shipshape/util/strings",
        "//shipshape/util/test",
        "@com_github_golang_protobuf//proto:go_default_library",
    ],
)
