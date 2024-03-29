cmake_minimum_required(VERSION 3.26)

#!!Notice
#------------------------------------------------------------------------#
#   this app need add a argument to the cmd line eg:FFPlay.exe 1.mp4     #
#------------------------------------------------------------------------#

project(FFMpeg)
#find Header File *.h
file(GLOB_RECURSE HEADER_FILES "${CMAKE_SOURCE_DIR}/*.h")
#fing lib File *.lib
file(GLOB SharedLibrary "${CMAKE_SOURCE_DIR}/lib/*.lib")
#output the msg to check the variable right or not?
#message(WARNING "${SharedLibrary}")
#set the Header File directory
source_group("Header Files" FILES ${HEADER_FILES})

#add the *.h file to the sln
include_directories(${CMAKE_SOURCE_DIR}/include ${CMAKE_SOURCE_DIR}/.)

#add the *.cpp/*.c file to the sln
aux_source_directory(${CMAKE_SOURCE_DIR}/. cppFile)

#set output direcory this will fill with debug or release when generate
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/OutPut)

#generate the application
add_executable(FFPlay ${cppFile} ${HEADER_FILES})
#add the app needed *.lib
target_link_libraries(FFPlay ${SharedLibrary})