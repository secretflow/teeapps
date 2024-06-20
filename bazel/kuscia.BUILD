# Copyright 2023 Ant Group Co., Ltd.
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

load("@rules_proto//proto:defs.bzl", "proto_library")
load("@rules_proto_grpc//cpp:defs.bzl", "cpp_grpc_library")

package(default_visibility = ["//visibility:public"])

proto_library(
    name = "kuscia_proto",
    srcs = glob([
        "proto/api/v1alpha1/*.proto",
        "proto/api/v1alpha1/**/*.proto",
    ]),
    import_prefix = "kuscia/",
    deps = [
        "@com_google_protobuf//:any_proto",
    ],
)

cpp_grpc_library(
    name = "cc_kuscia_proto",
    deps = [":kuscia_proto"],
)
