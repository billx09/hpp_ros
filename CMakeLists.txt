# Copyright (c) 2013 CNRS
# Author: Florent Lamiraux
#
# This file is part of hpp_ros.
# hpp_ros is free software: you can redistribute it
# and/or modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation, either version
# 3 of the License, or (at your option) any later version.
#
# hpp_ros is distributed in the hope that it will be
# useful, but WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Lesser Public License for more details.  You should have
# received a copy of the GNU Lesser General Public License along with
# hpp_ros.  If not, see
# <http://www.gnu.org/licenses/>.

cmake_minimum_required(VERSION 2.8.3)

project(hpp_ros)
include(cmake/base.cmake)
include(cmake/python.cmake)

set(PROJECT_DESCRIPTION
  "Bridge between hpp and ros."
)
set(PROJECT_URL "")

set(${PROJECT_NAME}_HEADERS
  include/hpp/ros/joint-state.hh
  include/hpp/ros/joint-trajectory.hh
  )

findpython()
setup_project()

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs rostime sensor_msgs tf)

catkin_package()

catkin_python_setup()

INSTALL (FILES
  src/hpp_ros/manipulation/__init__.py
  src/hpp_ros/manipulation/scene_publisher.py
  DESTINATION ${CATKIN_PACKAGE_PYTHON_DESTINATION}/manipulation
  )

install(FILES launch/hpp_ros.launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
  )

install(FILES rviz_configs/hpp_ros.rviz
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/rviz_configs
  )

setup_project_finalize()
