# SPDX-FileCopyrightText: Joshua Goins <josh@redstrate.com>
# SPDX-License-Identifier: BSD-2-Clause

cmake_minimum_required(VERSION 3.16)
project(QtBlurHash VERSION 1.0.0)

set(KF_MIN_VERSION "6.0.0")
set(QT_MIN_VERSION 6.0)

find_package(ECM ${KF_MIN_VERSION} REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${CMAKE_SOURCE_DIR}/cmake)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(KDEInstallDirs)
include(ECMAddTests)
include(KDECMakeSettings)
include(KDEClangFormat)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(KDEGitCommitHooks)

find_package(Qt6 REQUIRED Core Gui Quick Test)

add_library(blurhash_qt STATIC src/blurhash.cpp src/blurhash.h imageprovider/blurhashimageprovider.h imageprovider/blurhashimageprovider.cpp)
target_include_directories(blurhash_qt PUBLIC src/)
target_link_libraries(blurhash_qt PUBLIC Qt::Core Qt::Gui Qt::Quick)

add_subdirectory(autotests)

file(GLOB_RECURSE ALL_CLANG_FORMAT_SOURCE_FILES src/*.cpp src/*.h)
kde_clang_format(${ALL_CLANG_FORMAT_SOURCE_FILES})

kde_configure_git_pre_commit_hook(CHECKS CLANG_FORMAT)