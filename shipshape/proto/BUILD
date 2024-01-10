load("@io_bazel_rules_go//go:def.bzl", "go_library")
load("@rules_proto//proto:defs.bzl", "proto_library")
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
    name = "source_context_proto",
    srcs = ["source_context.proto"],
)

proto_library(
    name = "textrange_proto",
    srcs = ["textrange.proto"],
)

proto_library(
    name = "note_proto",
    srcs = ["note.proto"],
    deps = [
        ":source_context_proto",
        ":textrange_proto",
    ],
)

proto_library(
    name = "shipshape_context_proto",
    srcs = ["shipshape_context.proto"],
    deps = [
        ":source_context_proto",
#        "//third_party/kythe/proto:analysis_proto",
    ],
)

proto_library(
    name = "shipshape_rpc_proto",
    srcs = ["shipshape_rpc.proto"],
    deps = [
        ":note_proto",
        ":shipshape_context_proto",
    ],
)

proto_library(
    name = "shipshape_config_proto",
    srcs = ["shipshape_config.proto"],
)

proto_library(
    name = "shipshape_reporter_proto",
    srcs = ["shipshape_reporter.proto"],
    deps = [
        ":note_proto",
        ":shipshape_context_proto",
    ],
)

go_proto_library(
    name = "source_context_go_proto",
    importpath = "github.com/buildbuddy-io/shipshape/shipshape/proto/source_context",
    proto = ":source_context_proto",
)
