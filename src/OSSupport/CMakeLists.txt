
cmake_minimum_required (VERSION 2.6)
project (MCServer)

include_directories ("${PROJECT_SOURCE_DIR}/../")

SET (SRCS
	CriticalSection.cpp
	Errors.cpp
	Event.cpp
	File.cpp
	GZipFile.cpp
	IsThread.cpp
	ListenThread.cpp
	Semaphore.cpp
	Sleep.cpp
	Socket.cpp
	SocketThreads.cpp
	StackTrace.cpp
	Thread.cpp
	Timer.cpp
)

SET (HDRS
	CriticalSection.h
	Errors.h
	Event.h
	File.h
	GZipFile.h
	IsThread.h
	ListenThread.h
	Queue.h
	Semaphore.h
	Sleep.h
	Socket.h
	SocketThreads.h
	StackTrace.h
	Thread.h
	Timer.h
)

if(NOT MSVC)
	add_library(OSSupport ${SRCS} ${HDRS})

	if(UNIX)
		if(NOT APPLE)
			target_link_libraries(OSSupport rt)
		endif()

		target_link_libraries(OSSupport pthread)
	endif()
endif()
