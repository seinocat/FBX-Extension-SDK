SET(CMAKE_MIN_REQ_VERSION 2.4)
cmake_minimum_required(VERSION ${CMAKE_MIN_REQ_VERSION})

INCLUDE("CMakeSettings.txt")

IF(FBX_MAYA)
    SET(FBX_TARGET_SOURCE 
        ../../Code/maya/mayaextension.h
        ../../Code/maya/mayafbxmethod.h
        ../../Code/maya/mayatemplateplugin.cxx
        ../../Code/maya/mayafbxmethod.cxx  
    )
ELSEIF(FBX_3DSMAX)
    SET(FBX_TARGET_SOURCE 
        ../../Code/max/maxextension.h
        ../../Code/max/maxfbxmethod.h
        ../../Code/max/maxtemplateplugin.cxx
        ../../Code/max/maxfbxmethod.cxx
    )
ENDIF()

FBX_PROJECT(${FBXEXT_TARGET}_FbxExt .)
ADD_LIBRARY(${FBX_TARGET_NAME} SHARED ${FBX_TARGET_SOURCE})

SET_SAMPLES_GLOBAL_FLAGS()
