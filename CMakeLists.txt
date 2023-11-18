cmake_minimum_required(VERSION 3.10.0)
project(qtimageviewer VERSION 0.1.0 LANGUAGES C CXX)

set(QT_VERSION_BASE "Qt5")

# Find the QtWidgets library
find_package(${QT_VERSION_BASE} COMPONENTS Widgets Concurrent REQUIRED)

aux_source_directory(. SRC_FILES)

add_executable(qtimageviewer 
    ${SRC_FILES}
    imageviewer.qrc
    mainwindow.ui
    imageviewer.rc
)

set_target_properties(qtimageviewer PROPERTIES
    AUTOMOC ON
	AUTOUIC ON
	AUTORCC ON
)

target_link_libraries(qtimageviewer
	${QT_VERSION_BASE}::Widgets
	${QT_VERSION_BASE}::Concurrent
)

target_include_directories(qtimageviewer PRIVATE ./)