cmake_minimum_required(VERSION 3.11)

find_package(Boost 1.66 COMPONENTS system thread regex unit_test_framework REQUIRED)

set(BEASTHTTP_CHAIN_ROUTER_TEST_NAME chain_router_test)

include_directories(${BEASTHTTP_INCLUDE_PATH})
include_directories(${Boost_INCLUDE_DIRS})

set(SRCS chain_router.cxx)

add_executable(${BEASTHTTP_CHAIN_ROUTER_TEST_NAME} ${SRCS})

target_link_libraries(${BEASTHTTP_CHAIN_ROUTER_TEST_NAME} Boost::system Boost::thread
    Boost::regex Boost::unit_test_framework pthread icui18n)

add_test (NAME ${BEASTHTTP_CHAIN_ROUTER_TEST_NAME} COMMAND "${BEASTHTTP_CHAIN_ROUTER_TEST_NAME}" "--log_level=test_suite")
