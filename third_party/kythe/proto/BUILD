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

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

proto_library(
    name = "any_proto",
    srcs = ["any.proto"],
)

go_proto_library(
    name = "any_go_proto",
    importpath = "github.com/google/shipshape/third_party/kythe/proto/any_proto",
    proto = ":any_proto",
)

java_proto_library(
    name = "any_proto_java",
    deps = [":any_proto"],
)

proto_library(
    name = "storage_proto",
    srcs = ["storage.proto"],
)

go_proto_library(
    name = "storage_go_proto",
    importpath = "github.com/google/shipshape/third_party/kythe/proto/storage_proto",
    proto = ":storage_proto",
)

java_proto_library(
    name = "storage_proto_java",
    deps = [":storage_proto"],
)

proto_library(
    name = "analysis_proto",
    srcs = ["analysis.proto"],
    deps = [
        ":any_proto",
        ":storage_proto",
    ],
)

go_proto_library(
    name = "analysis_go_proto",
    importpath = "github.com/google/shipshape/third_party/kythe/proto/analysis_proto",
    proto = ":analysis_proto",
    deps = [
        ":any_go_proto",
        ":storage_go_proto",
    ],
)

java_proto_library(
    name = "analysis_proto_java",
    deps = [":analysis_proto"],
)
