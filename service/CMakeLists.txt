cmake_minimum_required(VERSION 2.8)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++11")
PROJECT(Service)
include_directories(
    src
    src-gen
    ~/vsomeip/capicxx-core-runtime/include
    ~/vsomeip/capicxx-someip-runtime/include
    ~/vsomeip/vSomeIP/interface
)
link_directories(
    ~/vsomeip/COMMONAPI
)
add_executable(HelloWorldService
    src/HelloWorldService.cpp
    src/HelloWorldStubImpl.cpp
    src-gen/v1/commonapi/HelloWorldSomeIPStubAdapter.cpp
    src-gen/v1/commonapi/HelloWorldStubDefault.cpp
    src-gen/v1/commonapi/HelloWorldSomeIPDeployment.cpp
)
target_link_libraries(HelloWorldService CommonAPI CommonAPI-SomeIP vsomeip)
