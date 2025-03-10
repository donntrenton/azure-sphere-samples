#  Copyright (c) Microsoft Corporation. All rights reserved.
#  Licensed under the MIT License.

cmake_minimum_required(VERSION 3.10)

project(ErrorReporting C)

azsphere_configure_tools(TOOLS_REVISION "21.10")
azsphere_configure_api(TARGET_API_SET "11")

add_executable(${PROJECT_NAME} main.c eventloop_timer_utilities.c)
target_link_libraries(${PROJECT_NAME} applibs gcc_s c)

# TARGET_HARDWARE and TARGET_DEFINITION relate to the hardware definition targeted by this tutorial.
# When using this tutorial with other hardware, replace TARGET_HARDWARE with the name of that hardware.
# For example, to target the Avnet MT3620 Starter Kit, use the value "avnet_mt3620_sk".
# See https://aka.ms/azsphere-samples-hardwaredefinitions for further details on this feature.
set(TARGET_HARDWARE "mt3620_rdb")
set(TARGET_DEFINITION "sample_appliance.json")

set(TARGET_DIRECTORY "../../../HardwareDefinitions/${TARGET_HARDWARE}")

azsphere_target_hardware_definition(${PROJECT_NAME} TARGET_DIRECTORY "${TARGET_DIRECTORY}" TARGET_DEFINITION "${TARGET_DEFINITION}")

azsphere_target_add_image_package(${PROJECT_NAME})
