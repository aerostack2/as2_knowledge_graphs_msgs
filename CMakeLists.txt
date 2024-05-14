cmake_minimum_required(VERSION 3.8)
set (PROJECT_NAME as2_knowledge_graph_msgs)
project(${PROJECT_NAME})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(PROJECT_DEPENDENCIES
  knowledge_graph_msgs
  )

  foreach(DEPENDENCY ${PROJECT_DEPENDENCIES})
  find_package(${DEPENDENCY} REQUIRED)
endforeach()

set(SRVS_FILES
  srv/CreateNode.srv
  srv/CreateEdge.srv
  srv/ReadGraph.srv
  srv/ReadEdgeGraph.srv
  srv/ReadProperty.srv
)


rosidl_generate_interfaces(${PROJECT_NAME}
  ${SRVS_FILES}
  DEPENDENCIES ${PROJECT_DEPENDENCIES}
)

ament_package()