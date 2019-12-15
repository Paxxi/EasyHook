cmake_minimum_required(VERSION 3.0)

project(easyhook)

add_custom_target(easyhook ALL COMMAND msbuild /m EasyHook.sln /p:Configuration=netfx4-Release /p:Platform=$(Platform) /target:EasyHookDll WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

if(CMAKE_SIZEOF_VOID_P EQUAL 4)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/Build/netfx4-Release/x64/EasyHook32.dll DESTINATION bin)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/Public/easyhook.h DESTINATION include/easyhook)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/Build/netfx4-Release/x64/EasyHook32.lib DESTINATION lib)
else()
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/Build/netfx4-Release/x64/EasyHook64.dll DESTINATION bin)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/Public/easyhook.h DESTINATION include/easyhook)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/Build/netfx4-Release/x64/EasyHook64.lib DESTINATION lib)
endif()