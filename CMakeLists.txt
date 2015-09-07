cmake_minimum_required(VERSION 3.3)
project(ForumMarkupTools)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES main.cpp)
add_executable(ForumMarkupTools ${SOURCE_FILES})

set(BOOST_ROOT /usr/local/Cellar/boost/1.57.0/)
set(BOOST_INCLUDEDIR /usr/local/Cellar/boost/1.57.0/include/boost/)
set(BOOST_LIBRARYDIR /usr/local/Cellar/boost/1.57.0/lib/)

set(Boost_USE_STATIC_LIBS   ON)
set(Boost_USE_DYNAMIC_LIBS   ON)
set(Boost_USE_MULTITHREADED ON)

find_package(Boost 1.57.0 COMPONENTS system regex REQUIRED)

if(Boost_FOUND)

    message(STATUS "Boost_INCLUDE_DIRS: ${Boost_INCLUDE_DIRS}")
    message(STATUS "Boost_LIBRARIES: ${Boost_LIBRARIES}")
    message(STATUS "Boost_VERSION: ${Boost_VERSION}")

    find_path (SPIRIT_INCLUDE_DIRS boost/spirit/include/version.hpp
            PATHS ${CMAKE_SOURCE_DIR}/../spirit ${Boost_INCLUDE_DIRS}
    )

    include_directories(${Boost_INCLUDE_DIRS})

endif()

if(Boost_FOUND)

    target_link_libraries(ForumMarkupTools ${Boost_LIBRARIES})

endif()