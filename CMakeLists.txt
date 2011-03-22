CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(SimpleAmqpClient)

#SET(Boost_DEBUG TRUE)
#SET(Boost_DETAILED_FAILURE_MSG TRUE)
SET(Boost_ADDITIONAL_VERSIONS "1.44.0")

FIND_PACKAGE(Boost 1.44.0 COMPONENTS thread REQUIRED)

SET(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/Modules)
FIND_PACKAGE(Rabbitmqc REQUIRED)

INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS}
					${Rabbitmqc_INCLUDE_DIRS}
					${CMAKE_CURRENT_SOURCE_DIR})

SET(SAC_LIB_SRCS
    Channel.h
    Channel.cpp

    BasicMessage.h
    BasicMessage.cpp

    Util.h
    Util.cpp

    AmqpResponseLibraryException.h
    AmqpResponseLibraryException.cpp

    AmqpResponseServerException.h
    AmqpResponseServerException.cpp

	SimpleRpcClient.h
	SimpleRpcClient.cpp

	SimpleRpcServer.h
	SimpleRpcServer.cpp

	SimplePublisher.h
	SimplePublisher.cpp

	SimpleSubscriber.h
	SimpleSubscriber.cpp

	SimpleTwoWayChannel.h
	SimpleTwoWayChannel.cpp

	UmroBrokerConfiguration.h
	UmroBrokerConfiguration.cpp
	)



ADD_LIBRARY(simple-amqp-client-static STATIC ${SAC_LIB_SRCS})
ADD_LIBRARY(simple-amqp-client-shared SHARED ${SAC_LIB_SRCS})

SET_TARGET_PROPERTIES(simple-amqp-client-static PROPERTIES OUTPUT_NAME SimpleAmqpClient)
SET_TARGET_PROPERTIES(simple-amqp-client-shared PROPERTIES OUTPUT_NAME SimpleAmqpClient)

TARGET_LINK_LIBRARIES(simple-amqp-client-shared ${Rabbitmqc_LIBRARY} ${Boost_LIBRARIES})

ADD_EXECUTABLE(simple_connect examples/simple_connect.cpp)

TARGET_LINK_LIBRARIES(simple_connect simple-amqp-client-shared)

ADD_EXECUTABLE(consume_with_timeout examples/consume_with_timeout.cpp)

TARGET_LINK_LIBRARIES(consume_with_timeout simple-amqp-client-shared)

# Documentation generation
SET(DOXYFILE_LATEX "NO")
SET(PROJECT_VERSION "1.0.0")
INCLUDE(UseDoxygen)