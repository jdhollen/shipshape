load("@io_bazel_rules_go//go:def.bzl", "go_binary", "go_library")

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
    name = "test_shipshape_client",
    embed = [":test_lib"],
)

java_binary(
    name = "test_request_via_stream",
    srcs = [
        "TestRequestViaStream.java",
    ],
    main_class = "test.TestRequestViaStream",
    deps = [
        "//shipshape/proto:note_proto_java",
        "//shipshape/proto:shipshape_context_proto_java",
        "//shipshape/proto:shipshape_rpc_proto_java",
        "//shipshape/proto:source_context_proto_java",
    ],
)

go_library(
    name = "test_lib",
    srcs = ["test_shipshape_client.go"],
    importpath = "github.com/google/shipshape/shipshape/test",
    deps = [
        "//shipshape/proto:shipshape_context_go_proto",
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/proto:source_context_go_proto",
        "//shipshape/util/file",
        "//shipshape/util/rpc/client",
        "@com_github_golang_protobuf//proto:go_default_library",
    ],
)
