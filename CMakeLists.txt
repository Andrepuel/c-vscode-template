cmake_minimum_required(VERSION 3.0)

project(my_app)
enable_testing()

add_library(my_library
    src/lib.c
    src/lib.h
)

add_executable(my_app
    src/main.c
)
target_link_libraries(my_app my_library)

add_executable(unit_tests
    tests/failing_test.c
    tests/failing_test.h
    tests/main.c
    tests/ok_test.c
    tests/ok_test.h
)
target_link_libraries(unit_tests my_library)

add_test(NAME unit_tests
         COMMAND ./unit_tests
         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)