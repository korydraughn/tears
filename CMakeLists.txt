cmake_minimum_required(VERSION 3.11.4 FATAL_ERROR)
project(tears LANGUAGES C)

set(PROJECT_NAME tears)
set(IRODS_CLIENT_C_INCLUDES_ROOT /home/kory/dev/prog/cpp/irods_client_library_c)
set(IRODS_CLIENT_C_LIBS_ROOT /home/kory/dev/prog/cpp/build_irods_client_library_c)

add_executable(${PROJECT_NAME} tears.c)

target_compile_definitions(${PROJECT_NAME}
                           PRIVATE
                           RODS_REL_VERSION="rods4.3.0"
                           RODS_API_VERSION="d"
                           IRODS_VERSION_MAJOR=4
                           IRODS_VERSION_MINOR=3
                           IRODS_VERSION_PATCHLEVEL=0)

target_compile_options(${PROJECT_NAME} PRIVATE -Wall)

target_include_directories(${PROJECT_NAME}
                           PRIVATE
                           ${IRODS_CLIENT_C_INCLUDES_ROOT}/include/api
                           ${IRODS_CLIENT_C_INCLUDES_ROOT}/include/core
                           ${IRODS_CLIENT_C_INCLUDES_ROOT}/include/hasher)

target_link_libraries(${PROJECT_NAME}
                      PRIVATE
                      ${IRODS_CLIENT_C_LIBS_ROOT}/libirods_client_c.so)

