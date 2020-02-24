cmake_minimum_required(VERSION 3.8)
project(NotificationSender)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

add_library(mail STATIC 3rdparty/libmail/src/send_mail.cpp)
target_include_directories(mail PUBLIC 3rdparty/libmail/include)

add_executable(app1 src/task1.cpp)
target_link_libraries(app1 PRIVATE mail Threads::Threads)
target_compile_options(app1 PRIVATE -Wall -Werror -Wpedantic -Wextra)

add_executable(app2 src/task2.cpp)
target_link_libraries(app2 PRIVATE mail Threads::Threads)
target_compile_options(app2 PRIVATE -Wall -Werror -Wpedantic -Wextra)

add_executable(app3 src/task3.cpp)
target_link_libraries(app3 PRIVATE mail Threads::Threads)
target_compile_options(app3 PRIVATE -Wall -Werror -Wpedantic -Wextra)