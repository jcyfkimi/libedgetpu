# Copyright 2019 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Description:
# Kernel driver specific functionality.

package(default_visibility = ["//visibility:public"])

licenses(["notice"])

cc_library(
    name = "kernel_mmu_mapper",
    srcs = ["kernel_mmu_mapper.cc"],
    hdrs = ["kernel_mmu_mapper.h"],
    deps = [
        ":linux_gasket_ioctl",
        "//driver:hardware_structures",
        "//driver/memory:dma_direction",
        "//driver/memory:mmu_mapper",
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
        "//port:tracing",
    ],
)

cc_library(
    name = "kernel_event",
    srcs = ["kernel_event.cc"],
    hdrs = ["kernel_event.h"],
    deps = [
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
        "//port:tracing",
    ],
)

cc_library(
    name = "kernel_event_handler",
    srcs = ["kernel_event_handler.cc"],
    hdrs = ["kernel_event_handler.h"],
    deps = [
        ":kernel_event",
        ":linux_gasket_ioctl",
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
        "//port:tracing",
    ],
)

cc_library(
    name = "kernel_interrupt_handler",
    srcs = ["kernel_interrupt_handler.cc"],
    hdrs = ["kernel_interrupt_handler.h"],
    deps = [
        "//driver/interrupt:interrupt_handler",
        "//driver/kernel:kernel_event_handler",
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
    ],
)

cc_library(
    name = "kernel_wire_interrupt_handler",
    srcs = ["kernel_wire_interrupt_handler.cc"],
    hdrs = ["kernel_wire_interrupt_handler.h"],
    deps = [
        ":kernel_event_handler",
        "//driver/config",
        "//driver/interrupt:interrupt_handler",
        "//driver/interrupt:wire_interrupt_handler",
        "//driver/registers",
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
    ],
)

cc_library(
    name = "kernel_coherent_allocator",
    srcs = ["kernel_coherent_allocator.cc"],
    hdrs = ["kernel_coherent_allocator.h"],
    deps = [
        ":linux_gasket_ioctl",
        "//driver:hardware_structures",
        "//driver/mmio:coherent_allocator",
        "//port",
    ],
)

cc_library(
    name = "kernel_registers",
    srcs = ["kernel_registers.cc"],
    hdrs = ["kernel_registers.h"],
    deps = [
        "@com_google_absl//absl/strings:str_format",
        "//driver/registers",
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
    ],
)

cc_library(
    name = "linux_gasket_ioctl",
    hdrs = ["linux_gasket_ioctl.h"],
)
