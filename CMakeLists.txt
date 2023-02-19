cmake_minimum_required(VERSION 3.15.1 FATAL_ERROR)

project(ObjcSwiftNinja LANGUAGES C CXX Swift)

add_compile_options(
    $<$<COMPILE_LANGUAGE:C,CXX>:-fcxx-modules>
    $<$<COMPILE_LANGUAGE:C,CXX>:-fmodules>
)

add_executable(${PROJECT_NAME}-app MACOSX_BUNDLE)

target_compile_options(${PROJECT_NAME}-app
     PRIVATE
         $<$<COMPILE_LANGUAGE:Swift>:-import-objc-header>
         $<$<COMPILE_LANGUAGE:Swift>:${CMAKE_CURRENT_SOURCE_DIR}/ObjcSwiftNinja-Bridging-Header.h>
)

target_sources(${PROJECT_NAME}-app
    PRIVATE
        main.m
        MyObjC.h
        MyObjC.m
        MySwift.swift
        ObjcSwiftNinja-Bridging-Header.h
)

set_target_properties(${PROJECT_NAME}-app
    PROPERTIES
        MACOSX_BUNDLE_GUI_IDENTIFIER "objc.swift.ninja"
        OUTPUT_NAME ObjcSwiftNinja
        Swift_LANGUAGE_VERSION "5"
        Swift_MODULE_NAME ObjcSwiftNinja
)
