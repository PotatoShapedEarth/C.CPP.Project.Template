get_filename_component(ProjectId ${CMAKE_CURRENT_SOURCE_DIR} NAME)
string(REPLACE " " "_" ProjectId ${ProjectId})
project(${ProjectId})

file(GLOB PROJECT_FILES *.h *.hpp *.c *.cpp)


#? PLEASE READ UNTIL THE END OF THE COMMENTS

# If you want to add project files located in subdirectories
# uncomment this line below and change "SUBPROJECT" with the name of your choosing and "your_folder_here" with you subdirectory's name
# file(GLOB SUBPROJECT_FILES your_folder_here/*.h your_folder_here/*.hpp your_folder_here/*.c your_folder_here/*.cpp)
# you can copy this line for each subdirectory

# You must then add it to the line below in the format comment below (you do it for each subfolder)
set(${ProjectId}_FILES ${PROJECT_FILES} #${SUBPROJECT_FILES}
	)


if(WIN32)
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

add_library(${ProjectId} STATIC ${PROJECT_FILES})
target_include_directories(${ProjectId} PRIVATE ${CMAKE_CURRENT_LIST_DIR}/)