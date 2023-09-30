project(uWebSocketsCMake)

add_library(uWebSockets
    Epoll.cpp
    Extensions.cpp
    Group.cpp
    HTTPSocket.cpp
    Hub.cpp
    Networking.cpp
    Node.cpp
    Room.cpp
    Socket.cpp
    WebSocket.cpp
)
add_library(uWebSockets::uWebSockets ALIAS uWebSockets)
# target_link_libraries(uWebSockets PUBLIC )

target_include_directories(uWebSockets PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../include/uWebSockets)

install(TARGETS uWebSockets
                RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
                ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
                LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})