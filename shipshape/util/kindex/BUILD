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
    name = "kindex_printer",
    embed = [":kindex_lib"],
)

go_library(
    name = "kindex_lib",
    srcs = ["kindex.go"],
    importpath = "github.com/google/shipshape/shipshape/util/kindex",
    deps = ["//third_party/kythe/go/platform/kindex"],
)
