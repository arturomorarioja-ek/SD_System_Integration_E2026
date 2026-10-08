## Warehouse Robot Service

A logistics company operates a warehouse with autonomous robots that move boxes between storage areas, packing stations, and loading zones. The warehouse control system exposes a gRPC API used internally by:
- Robot controllers
- Warehouse management software
- Monitoring dashboards

The API must allow clients to:
- Assign a task to a robot
- Retrieve the status of a robot
- Mark a task as completed

Write the corresponding `warehouse_robot_service.proto` file.

**Functional requirements**

1. Assign a task to a robot

    - A client sends `robot_id`, `task_id`, `pickup_zone`, `delivery_zone`, `box_id`
    - The server returns: `confirmation_message`, `assigned_task_id`

2. Get robot status

    - A client sends: `robot_id`
    - The server returns: `robot_id`, `current_zone`, `battery_level`, `status`

3. Complete a task

    - A client sends: `task_id`, `robot_id`
    - The server returns: `confirmation_message`

Define an enum for robot `status`: `IDLE`, `MOVING`, `CHARGING`, `ERROR`.

## Solution

```proto
syntax = "proto3";

package warehouse_robot;

service WarehouseRobotService {
  rpc AssignTask(AssignTaskRequest) returns (AssignTaskResponse);
  rpc GetRobotStatus(GetRobotStatusRequest) returns (GetRobotStatusResponse);
  rpc CompleteTask(CompleteTaskRequest) returns (CompleteTaskResponse);
}

message AssignTaskRequest {
  string robot_id = 1;
  string task_id = 2;
  string pickup_zone = 3;
  string delivery_zone = 4;
  string box_id = 5;
}

message AssignTaskResponse {
  string confirmation_message = 1;
  string assigned_task_id = 2;
}

message GetRobotStatusRequest {
  string robot_id = 1;
}

message GetRobotStatusResponse {
  string robot_id = 1;
  string current_zone = 2;
  int32 battery_level = 3;
  RobotStatus status = 4;
}

message CompleteTaskRequest {
  string task_id = 1;
  string robot_id = 2;
}

message CompleteTaskResponse {
  string confirmation_message = 1;
}

enum RobotStatus {
  ROBOT_STATUS_UNSPECIFIED = 0;
  IDLE = 1;
  MOVING = 2;
  CHARGING = 3;
  ERROR = 4;
}
```
