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
    name = "shipshape",
    srcs = ["shipshape.go"],
    deps = [
        ":cli",
        "//shipshape/proto:note_go_proto",
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/util/defaults",
    ],
)

go_library(
    name = "cli",
    srcs = ["shipshape_lib.go"],
    importpath = "github.com/google/shipshape/shipshape/cli",
    deps = [
        "//shipshape/proto:shipshape_context_go_proto",
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/service",
        "//shipshape/util/docker",
        "//shipshape/util/rpc/client",
        "//third_party/go-glog",
        "@com_github_golang_protobuf//proto:go_default_library",
    ],
)

go_test(
    name = "test_prod",
    srcs = ["shipshape_test.go"],
    args = [
        "--shipshape_test_docker_tag=prod",
    ],
    data = [
        "testdata",
    ],
    embed = [":cli"],
    tags = ["manual"],
    deps = [
        "//shipshape/util/docker",
    ],
)

go_test(
    name = "test_staging",
    srcs = ["shipshape_test.go"],
    args = [
        "--shipshape_test_docker_tag=staging",
    ],
    data = [
        "testdata",
    ],
    embed = [":cli"],
    tags = ["manual"],
)

go_test(
    name = "test_local",
    srcs = ["shipshape_test.go"],
    args = [
        "--shipshape_test_docker_tag=local",
    ],
    data = [
        "testdata",
        # TODO(rsk): figure out why we need to rely on the output
        # marker rather than the target name (may be a bug in
        # either Bazel or the docker_build extension).
        "//shipshape/docker:service.done",
        "//shipshape/androidlint_analyzer/docker:android_lint.done",
    ],
    embed = [":cli"],
    # Because the docker images are manual, we want to make this
    # manual as well or we'll end up building the docker images
    # from a wildcard build.
    tags = ["manual"],
    deps = [
        "//shipshape/util/docker",
    ],
)

go_test(
    name = "cli_test",
    srcs = ["shipshape_test.go"],
    embed = [":cli"],
    deps = [
        "//shipshape/proto:shipshape_rpc_go_proto",
        "//shipshape/util/defaults",
        "//shipshape/util/docker",
    ],
)
