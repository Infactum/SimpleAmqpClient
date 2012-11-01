Changes since v2.0-beta
 - Add wrapping of amqp_table_t for passing table arguments to various
   AMQP RPC methods (bae7b97)
 - Fix for bug in BasicConsumeMessage default timeout (6412fcf3)
 - Enable travis-ci continuous integration (44089d65)
 - Ship google-test framework with library (8d86d2e4)
 - Implement SOVERSION-ing (b44f3b7b)
 - Missing include in AmqpException.cpp (20ccca9)
 - Fix for memory leak in BasicPublish when exception is thrown (56e20b2)
 - Fix for memory leak in BasicMessage when new body assigned (e5bf1157)
 - Missing string.h include in AmqpException.h (ecee2104)
 - Compile changes to compile cleanly under -Wall -Wextra (2b5a1a23)
 - Fix for crash when AmqpException thrown without a class or method id (6a4fac62)
 - Fix for incorrect timeout units when BasicConsumeMessage (3cdf94d9)
 - Relicensed library under MIT license (a069444b)
 - Fix sending unitialized data to broker (080bd9e9)
 - Fix free strings returned by amqp_error_string (c7b0cfcc)
 - Fix destroy amqp_connection_state object if an exception is thrown in Channel constructor (af936d0)
 - Add ability to build as static library (50b6afd)
 - Fix for macro redefinition (548084)
 - Correct usage of stdint.h on VS2008 and earlier (795c0fea)
