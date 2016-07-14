# Copyright 2013-2016, Corvusoft Ltd, All Rights Reserved.

project( "example" )

cmake_minimum_required( VERSION 2.8.10 )

#
# Configuration
#
set( EXECUTABLE_OUTPUT_PATH "${CMAKE_CURRENT_BINARY_DIR}/example/${CMAKE_BUILD_TYPE}" )

#
# Build
#
add_executable( basic_authentication basic_authentication/source/example.cpp )
target_link_libraries( basic_authentication ${TRGT} )

add_executable( authentication authentication/source/example.cpp )
target_link_libraries( authentication ${TRGT} )

add_executable( custom_status_codes custom_status_codes/source/example.cpp )
target_link_libraries( custom_status_codes ${TRGT} )

add_executable( digest_authentication digest_authentication/source/example.cpp )
target_link_libraries( digest_authentication ${TRGT} )

add_executable( error_handling error_handling/source/example.cpp )
target_link_libraries( error_handling ${TRGT} )

add_executable( logging logging/source/example.cpp )
target_link_libraries( logging ${TRGT} )

add_executable( path_parameters path_parameters/source/example.cpp )
target_link_libraries( path_parameters ${TRGT} )

add_executable( publishing_resources publishing_resources/source/example.cpp )
target_link_libraries( publishing_resources ${TRGT} )

add_executable( custom_methods custom_methods/source/example.cpp )
target_link_libraries( custom_methods ${TRGT} )

add_executable( publishing_multipath_resources publishing_multipath_resources/source/example.cpp )
target_link_libraries( publishing_multipath_resources ${TRGT} )

add_executable( resource_filtering resource_filtering/source/example.cpp )
target_link_libraries( resource_filtering ${TRGT} )

add_executable( serving_html serving_html/source/example.cpp )
target_link_libraries( serving_html ${TRGT} )

add_executable( transfer_encoding_request transfer_encoding_request/source/example.cpp )
target_link_libraries( transfer_encoding_request ${TRGT} )

add_executable( transfer_encoding_response transfer_encoding_response/source/example.cpp )
target_link_libraries( transfer_encoding_response ${TRGT} )

add_executable( persistent_connection persistent_connection/source/example.cpp )
target_link_libraries( persistent_connection ${TRGT} )

add_executable( compression compression/source/example.cpp )
target_link_libraries( compression ${TRGT} )

add_executable( http_service http_service/source/example.cpp )
target_link_libraries( http_service ${TRGT} )

add_executable( service_ready_handler service_ready_handler/source/example.cpp )
target_link_libraries( service_ready_handler ${TRGT} )

add_executable( session_data session_data/source/example.cpp )
target_link_libraries( session_data ${TRGT} )

add_executable( rules_engine rules_engine/source/example.cpp )
target_link_libraries( rules_engine ${TRGT} )

add_executable( multithreaded_service multithreaded_service/source/example.cpp )
target_link_libraries( multithreaded_service ${TRGT} )

add_executable( schedule_work_on_service_runloop schedule_work_on_service_runloop/source/example.cpp )
target_link_libraries( schedule_work_on_service_runloop ${TRGT} )

add_executable( bind_service_address bind_service_address/source/example.cpp )
target_link_libraries( bind_service_address ${TRGT} )

add_executable( session_manager session_manager/source/example.cpp )
target_link_libraries( session_manager ${TRGT} )

add_executable( http_client http_client/source/example.cpp )
target_link_libraries( http_client ${TRGT} )

add_executable( signal_handling signal_handling/source/example.cpp )
target_link_libraries( signal_handling ${TRGT} )

if ( PAM_FOUND )
    add_executable( pam_authentication pam_authentication/source/example.cpp )
    target_link_libraries( pam_authentication ${TRGT} pam )
endif ( )

if ( SYSLOG_FOUND )
    add_executable( syslog_logging syslog_logging/source/example.cpp )
    target_link_libraries( syslog_logging ${TRGT} )
endif ( )

if ( BUILD_SSL )
    add_executable( https_service https_service/source/example.cpp )
    target_link_libraries( https_service ${TRGT} )

    add_executable( https_client_verify_none https_client/source/verify_none.cpp )
    target_link_libraries( https_client_verify_none ${TRGT} )

    add_executable( https_client_verify_peer https_client/source/verify_peer.cpp )
    target_link_libraries( https_client_verify_peer ${TRGT} )
endif ( )

#
# Install
#
install( DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/example" DESTINATION ${CMAKE_INSTALL_PREFIX} FILE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE )

install( DIRECTORY "${CMAKE_SOURCE_DIR}/example/https_client/resource/certificates" DESTINATION "${CMAKE_INSTALL_PREFIX}/resource" FILE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE )

install( FILES "${CMAKE_SOURCE_DIR}/example/serving_html/resource/index.html" DESTINATION "resource" )
install( FILES "${CMAKE_SOURCE_DIR}/example/compression/resource/data.zlib" DESTINATION "resource" )
install( FILES "${CMAKE_SOURCE_DIR}/example/transfer_encoding_request/resource/request.txt" DESTINATION "resource" )
