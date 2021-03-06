###########################################################################
#
#  Library: MSVTK
#
#  Copyright (c) Kitware Inc.
#
#  Licensed under the Apache License, Version 2.0 (the "License");
#  you may not use this file except in compliance with the License.
#  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0.txt
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.
#
###########################################################################

set(KIT GridViewer)
set(KIT_TEST_SRCS
  GridViewerTest1.cxx
  msvQGridViewerMainWindowTest1.cxx
  )

create_test_sourcelist(Tests msv${KIT}CxxTests.cxx
  ${KIT_TEST_SRCS}
  )

set(LIBRARY_NAME msv${KIT})

add_executable(msv${KIT}CxxTests ${Tests})
target_link_libraries(msv${KIT}CxxTests ${LIBRARY_NAME})

#
# Add Tests
#

msv_test(GridViewerTest1
  $<TARGET_FILE:msv${KIT}CxxTests> GridViewerTest1
    --GridViewer $<TARGET_FILE_DIR:msv${KIT}CxxTests>
  )
simple_test( msvQGridViewerMainWindowTest1 )
