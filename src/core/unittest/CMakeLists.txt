# Copyright (c) Microsoft Corporation.
# Licensed under the MIT License.

set(SOURCES
    main.cpp
    FrameTest.cpp
    PacketNumberTest.cpp
    RangeTest.cpp
    SpinFrame.cpp
    TransportParamTest.cpp
    VarIntTest.cpp
)

# Allow CLOG to preprocess all the source files.
add_clog_library(msquiccoretest.clog STATIC ${SOURCES})

add_executable(msquiccoretest ${SOURCES})

target_include_directories(msquiccoretest PRIVATE ${PROJECT_SOURCE_DIR}/src/core)

set_property(TARGET msquiccoretest PROPERTY FOLDER "tests")

target_link_libraries(msquiccoretest msquic core platform inc gtest msquiccoretest.clog)

add_test(msquiccoretest msquiccoretest)
