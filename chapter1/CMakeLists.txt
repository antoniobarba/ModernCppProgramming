cmake_minimum_required(VERSION 3.29)
project(chapter1)
project(chapter1 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)   
add_executable(chapter1 src/main.cc)

option(ENABLE_TESTS "Enable Google Test suites" On)


if(ENABLE_TESTS)
    enable_testing()
    find_package(GTest REQUIRED)

    add_executable(
        chapter1_test
        test/test_main.cc
    )
    
    target_link_libraries(
        chapter1_test
        GTest::gtest_main
    )

    gtest_discover_tests(chapter1_test)

endif()
