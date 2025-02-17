function(LibraryLinker Target_exec)
    # Get all directories inside TARGET_DIR
    file(GLOB SUBDIRS LIST_DIRECTORIES true "${CMAKE_SOURCE_DIR}/libraries/*")
    # Link the library to the executable WITH FOR LOOP
    foreach(DIR ${SUBDIRS})
        if(IS_DIRECTORY ${DIR})
            get_filename_component(LIB_NAME ${DIR} NAME)
            target_link_libraries(${Target_exec} ${LIB_NAME})
        endif()
    endforeach()
endfunction()


file(GLOB SUBDIRS LIST_DIRECTORIES true "${CMAKE_CURRENT_SOURCE_DIR}/*")
foreach(dir ${SUBDIRS})
    if(IS_DIRECTORY ${dir})
        add_subdirectory(${dir})
    endif()
endforeach()