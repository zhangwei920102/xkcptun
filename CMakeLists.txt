cmake_minimum_required(VERSION 2.6)

project(xkcptun C)

set(src_xkcp_svr_demo
	xkcp_svr_demo.c
	xkcp_util.c
	xkcp_config.c
	commandline.c
	debug.c
	ikcp.c)
	
set(src_xkcp_server
	xkcp_server.c
	tcp_client.c
	debug.c
	ikcp.c
	commandline.c
	xkcp_util.c
	xkcp_config.c)
	
set(src_xkcp_client
	tcp_proxy.c
	xkcp_client.c
	xkcp_config.c
	xkcp_util.c
	commandline.c
	debug.c
	ikcp.c)

set(libs
	event
	json-c)

ADD_DEFINITIONS(-O2 -Wall --std=gnu99 -Wmissing-declarations)

add_executable(xkcp_client ${src_xkcp_client})
target_link_libraries(xkcp_client ${libs})

add_executable(xkcp_server ${src_xkcp_server})
target_link_libraries(xkcp_server ${libs})

add_executable(xkcp_svr_demo ${src_xkcp_svr_demo})
target_link_libraries(xkcp_svr_demo ${libs})

install(TARGETS xkcp_client xkcp_svr_demo
        RUNTIME DESTINATION bin
)
