cmake_minimum_required(VERSION 3.5)
project(humanoid_nav_msgs)

#List to make rest of code more readable
set( MESSAGE_DEPENDENCIES std_msgs geometry_msgs actionlib_msgs)

find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(actionlib_msgs REQUIRED)

find_package(rosidl_default_generators REQUIRED)

set(MSG_FILES msg/StepTarget.msg)
set(ACTION_FILES action/ExecFootsteps.action)
set(SRV_FILES
    srv/ClipFootstep.srv
    srv/PlanFootsteps.srv
    srv/PlanFootstepsBetweenFeet.srv
    srv/StepTargetService.srv
)

rosidl_generate_interfaces(${PROJECT_NAME}
    ${MSG_FILES}
    ${ACTION_FILES}
    ${SRV_FILES}
    DEPENDENCIES ${MESSAGE_DEPENDENCIES}
)

ament_package()