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
#  Beagle Specific functionality.

package(default_visibility = ["//visibility:public"])

licenses(["notice"])

# Provides Beagle USB Driver for internal (=no_external_release) usage.
# libUSB is statically linked in this version.
cc_library(
    name = "beagle_usb_driver_provider_no_external_release",
    srcs = ["beagle_usb_driver_provider.cc"],
    deps = [
        ":beagle_top_level_handler",
        ":beagle_top_level_interrupt_manager",
        "@com_google_absl//absl/strings",
        "//api:chip",
        "//api:driver",
        "//api:driver_options_fbs",
        "//driver:allocator",
        "//driver:driver_factory",
        "//driver:package_registry",
        "//driver:package_verifier",
        "//driver:run_controller",
        "//driver:scalar_core_controller",
        "//driver/config/beagle:beagle_chip_config",
        "//driver/interrupt:grouped_interrupt_controller",
        "//driver/interrupt:interrupt_controller",
        "//driver/interrupt:interrupt_controller_interface",
        "//driver/memory:null_dram_allocator",
        "//driver/time_stamper:driver_time_stamper",
        "//driver/usb:local_usb_device_no_external_release",
        "//driver/usb:usb_device_interface",
        "//driver/usb:usb_driver",
        "//driver/usb:usb_ml_commands",
        "//driver/usb:usb_registers",
        "//port",
        "//port:tracing",
    ],
    alwayslink = 1,
)

# Provides Beagle USB Driver.
# libUSB is dynamically linked in this version.
cc_library(
    name = "beagle_usb_driver_provider",
    srcs = ["beagle_usb_driver_provider.cc"],
    deps = [
        ":beagle_top_level_handler",
        ":beagle_top_level_interrupt_manager",
        "@com_google_absl//absl/strings",
        "//api:chip",
        "//api:driver",
        "//api:driver_options_fbs",
        "//driver:allocator",
        "//driver:driver_factory",
        "//driver:package_registry",
        "//driver:package_verifier",
        "//driver:run_controller",
        "//driver:scalar_core_controller",
        "//driver/config/beagle:beagle_chip_config",
        "//driver/interrupt:grouped_interrupt_controller",
        "//driver/interrupt:interrupt_controller",
        "//driver/interrupt:interrupt_controller_interface",
        "//driver/memory:null_dram_allocator",
        "//driver/time_stamper:driver_time_stamper",
        "//driver/usb:local_usb_device",
        "//driver/usb:usb_device_interface",
        "//driver/usb:usb_driver",
        "//driver/usb:usb_ml_commands",
        "//driver/usb:usb_registers",
        "//port",
        "//port:tracing",
    ],
    alwayslink = 1,
)

# Provides Beagle PCI Driver.
cc_library(
    name = "beagle_pci_driver_provider",
    srcs = ["beagle_pci_driver_provider.cc"],
    deps = [
        ":beagle_kernel_top_level_handler",
        "//api:chip",
        "//api:driver",
        "//driver:allocator",
        "//driver:driver_factory",
        "//driver:hardware_structures",
        "//driver:mmio_driver",
        "//driver:package_registry",
        "//driver:package_verifier",
        "//driver:run_controller",
        "//driver:scalar_core_controller",
        "//driver/config",
        "//driver/config/beagle:beagle_chip_config",
        "//driver/interrupt:dummy_interrupt_controller",
        "//driver/interrupt:grouped_interrupt_controller",
        "//driver/interrupt:interrupt_handler",
        "//driver/interrupt:top_level_interrupt_manager",
        "//driver/kernel:kernel_coherent_allocator",
        "//driver/kernel:kernel_interrupt_handler",
        "//driver/kernel:kernel_mmu_mapper",
        "//driver/kernel:kernel_registers",
        "//driver/kernel:kernel_wire_interrupt_handler",
        "//driver/memory:dual_address_space",
        "//driver/memory:null_dram_allocator",
        "//driver/mmio:host_queue",
        "//driver/time_stamper:driver_time_stamper",
        "//port",
    ],
    alwayslink = 1,
)

# Provides Beagle USB/PCI Driver. Used by an Android side script to
# populate dependencies for a unified Beagle provider in Beagle NNAPI HAL.
cc_library(
    name = "beagle_all_driver_provider",
    srcs = [
        "beagle_pci_driver_provider.cc",
        "beagle_usb_driver_provider.cc",
    ],
    deps = [
        ":beagle_kernel_top_level_handler",
        ":beagle_top_level_handler",
        ":beagle_top_level_interrupt_manager",
        "@com_google_absl//absl/strings",
        "//api:chip",
        "//api:driver",
        "//api:driver_options_fbs",
        "//driver:allocator",
        "//driver:driver_factory",
        "//driver:hardware_structures",
        "//driver:mmio_driver",
        "//driver:package_registry",
        "//driver:package_verifier",
        "//driver:run_controller",
        "//driver:scalar_core_controller",
        "//driver/config",
        "//driver/config/beagle:beagle_chip_config",
        "//driver/interrupt:dummy_interrupt_controller",
        "//driver/interrupt:grouped_interrupt_controller",
        "//driver/interrupt:interrupt_controller",
        "//driver/interrupt:interrupt_controller_interface",
        "//driver/interrupt:interrupt_handler",
        "//driver/interrupt:top_level_interrupt_manager",
        "//driver/kernel:kernel_coherent_allocator",
        "//driver/kernel:kernel_interrupt_handler",
        "//driver/kernel:kernel_mmu_mapper",
        "//driver/kernel:kernel_registers",
        "//driver/kernel:kernel_wire_interrupt_handler",
        "//driver/memory:dual_address_space",
        "//driver/memory:null_dram_allocator",
        "//driver/mmio:host_queue",
        "//driver/time_stamper:driver_time_stamper",
        "//driver/usb:local_usb_device",
        "//driver/usb:usb_device_interface",
        "//driver/usb:usb_driver",
        "//driver/usb:usb_ml_commands",
        "//driver/usb:usb_registers",
        "//port",
        "//port:tracing",
    ],
    alwayslink = 1,
)

cc_library(
    name = "beagle_top_level_interrupt_manager",
    srcs = ["beagle_top_level_interrupt_manager.cc"],
    hdrs = ["beagle_top_level_interrupt_manager.h"],
    deps = [
        "//driver/config",
        "//driver/interrupt:interrupt_controller_interface",
        "//driver/interrupt:top_level_interrupt_manager",
        "//driver/registers",
        "//port",
    ],
)

cc_library(
    name = "beagle_top_level_handler",
    srcs = ["beagle_top_level_handler.cc"],
    hdrs = ["beagle_top_level_handler.h"],
    deps = [
        "//api:driver_options_fbs",
        "//driver:top_level_handler",
        "//driver/config",
        "//driver/registers",
        "//port",
    ],
)

cc_library(
    name = "beagle_ioctl",
    hdrs = ["beagle_ioctl.h"],
)

cc_library(
    name = "beagle_kernel_top_level_handler",
    srcs = ["beagle_kernel_top_level_handler.cc"],
    hdrs = ["beagle_kernel_top_level_handler.h"],
    deps = [
        ":beagle_ioctl",
        "//api:driver_options_fbs",
        "//driver:top_level_handler",
        "//port",
        "//port:std_mutex_lock",
        "//port:thread_annotations",
    ],
)

# Standalone shared library that can be linked into a binary built elsewhere.
cc_binary(
    name = "libbeagle-usb.so",

    # Setting DT_SONAME for the result .so.
    # See b/72234056
    linkopts = [
        "-Wl,-soname,libbeagle-usb.so",
        "-Wl,--version-script=$(location //driver:libdarwinn_driver.lds)",
    ],
    linkshared = 1,
    linkstatic = 1,
    deps = [
        ":beagle_usb_driver_provider",
        "//driver:libdarwinn_driver.lds",
    ],
)

# Standalone shared library that can be linked into a binary built elsewhere.
cc_binary(
    name = "libbeagle-pci.so",

    # Setting DT_SONAME for the result .so.
    # See b/72234056
    linkopts = [
        "-Wl,-soname,libbeagle-pci.so",
        "-Wl,--version-script=$(location //driver:libdarwinn_driver.lds)",
    ],
    linkshared = 1,
    linkstatic = 1,
    deps = [
        ":beagle_pci_driver_provider",
        "//driver:libdarwinn_driver.lds",
    ],
)
