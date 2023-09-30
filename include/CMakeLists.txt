project(uWebSocketsCMake)

target_include_directories(uWebSockets PUBLIC
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>)

target_sources(uWebSockets PRIVATE
    # Header files (useful in IDEs)
    uWebSockets/Asio.h
    uWebSockets/Backend.h
    uWebSockets/Epoll.h
    uWebSockets/Extensions.h
    uWebSockets/Group.h
    uWebSockets/HTTPSocket.h
    uWebSockets/Hub.h
    uWebSockets/Libuv.h
    uWebSockets/Networking.h
    uWebSockets/Node.h
    uWebSockets/Room.h
    uWebSockets/Socket.h
    uWebSockets/uWS.h
    uWebSockets/WebSocket.h
    uWebSockets/WebSocketProtocol.h
)

install(DIRECTORY uWebSockets DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})