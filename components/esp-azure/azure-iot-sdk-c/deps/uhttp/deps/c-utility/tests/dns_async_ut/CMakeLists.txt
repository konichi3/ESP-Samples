#Copyright (c) Microsoft. All rights reserved.
#Licensed under the MIT license. See LICENSE file in the project root for full license information.

cmake_minimum_required(VERSION 2.8.11)

set(theseTestsName dns_async_ut)

set(${theseTestsName}_test_files
${theseTestsName}.c
)

set(${theseTestsName}_c_files
../../pal/dns_async.c
../../src/crt_abstractions.c
)

set(${theseTestsName}_h_files
)

include_directories(.)
include_directories(../../pal/inc)

if(WIN32)
	include_directories(./win32_fake_linux)
else()
	include_directories(../../pal/linux)
endif()

build_c_test_artifacts(${theseTestsName} ON "tests/azure_c_shared_utility_tests")

compile_c_test_artifacts_as(${theseTestsName} C99)
