SET(CMAKE_MIN_REQ_VERSION 2.4)
cmake_minimum_required(VERSION ${CMAKE_MIN_REQ_VERSION})

INCLUDE("CMakeSettings.txt")

IF(FBX_MAYA)
    SET(FBX_TARGET_SOURCE 
        ../../Code/mayaextension.h
        ../../Code/mayatemplateplugin.cxx  )
ELSEIF(FBX_3DSMAX)
    SET(FBX_TARGET_SOURCE 
        ../../Code/maxextension.h
        ../../Code/maxtemplateplugin.cxx
    )
ENDIF()

FBX_PROJECT(${FBXEXT_TARGET}_FBXExt .)
ADD_LIBRARY(${FBX_TARGET_NAME} SHARED ${FBX_TARGET_SOURCE})

SET_SAMPLES_GLOBAL_FLAGS()
