
cmake_minimum_required(VERSION 3.16)


project(QmlPlayer LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


find_package(Qt6 REQUIRED COMPONENTS Quick Multimedia Network)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)


set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)


set(RESOURCES resources.qrc)

add_executable(${PROJECT_NAME}
    main.cpp
    ${RESOURCES}
)


target_link_libraries(${PROJECT_NAME} PRIVATE
    Qt6::Quick
    Qt6::Multimedia
    Qt6::Network
)

set(QML_IMPORT_PATH ${PROJECT_SOURCE_DIR}/qml CACHE STRING "QML 导入路径" FORCE)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)