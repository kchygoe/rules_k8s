# Copyright 2017 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("@bazel_gazelle//:def.bzl", "gazelle")
load("@rules_python//python:pip.bzl", "compile_pip_requirements")

package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # Apache 2.0

exports_files([
    "LICENSE",
    "__init__.py",
])

gazelle(
    name = "gazelle",
    prefix = "github.com/bazelbuild/rules_k8s",
)

compile_pip_requirements(
    name = "pip",
    extra_args = ["--allow-unsafe"],
    requirements_in = "//:requirements.txt",
    requirements_txt = "//:requirements_lock.txt",
)

# Make Gazelle ignore Go files in the examples directory used in e2e tests.
# gazelle:exclude examples

# rules_docker's BUILD files follow the go_default_library naming convention
# gazelle:go_naming_convention_external go_default_library
