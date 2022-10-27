cmake_minimum_required(VERSION 2.8)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++0x")
Project(Client)
include_directories(
    src-gen
    ~/vsomeip/capicxx-core-runtime/include
    ~/vsomeip/capicxx-someip-runtime/include
    ~/vsomeip/vSomeIP/interface
)
link_directories(
    ~/vsomeip/COMMONAPI
)
add_executable(HelloWorldClient
    src/HelloWorldClient.cpp
    src-gen/v1/commonapi/HelloWorldSomeIPProxy.cpp
    src-gen/v1/commonapi/HelloWorldSomeIPDeployment.cpp
)
target_link_libraries(HelloWorldClient CommonAPI CommonAPI-SomeIP vsomeip)

