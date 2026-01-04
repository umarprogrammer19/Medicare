# Task Management API Contract

## Overview
This contract defines the interface for task management operations in the CLI Todo application.

## Operations

### Create Task
- **Method**: create_task(title: str, description: str = "", priority: str = "medium") -> Task
- **Input**:
  - title (str, required): Task title (1-200 characters)
  - description (str, optional): Task description (0-1000 characters)
  - priority (str, optional): Priority level ("high", "medium", "low") - defaults to "medium"
- **Output**: Task object with all fields populated
- **Success**: Returns created Task object with unique ID and timestamps
- **Errors**:
  - ValueError if title is empty or exceeds 200 characters
  - ValueError if priority is not one of allowed values

### Get Task
- **Method**: get_task(task_id: str) -> Task
- **Input**:
  - task_id (str, required): Unique identifier of the task
- **Output**: Task object
- **Success**: Returns the requested Task object
- **Errors**:
  - ValueError if task with given ID does not exist

### List Tasks
- **Method**: list_tasks(completed: Optional[bool] = None, priority: Optional[str] = None) -> List[Task]
- **Input**:
  - completed (bool, optional): Filter by completion status
  - priority (str, optional): Filter by priority level
- **Output**: List of Task objects
- **Success**: Returns filtered list of Task objects
- **Errors**: None

### Update Task
- **Method**: update_task(task_id: str, title: Optional[str] = None, description: Optional[str] = None, priority: Optional[str] = None, completed: Optional[bool] = None) -> Task
- **Input**:
  - task_id (str, required): Unique identifier of the task
  - title (str, optional): New title for the task
  - description (str, optional): New description for the task
  - priority (str, optional): New priority level
  - completed (bool, optional): New completion status
- **Output**: Updated Task object
- **Success**: Returns the updated Task object with updated timestamp
- **Errors**:
  - ValueError if task with given ID does not exist
  - ValueError if priority is not one of allowed values

### Delete Task
- **Method**: delete_task(task_id: str) -> bool
- **Input**:
  - task_id (str, required): Unique identifier of the task
- **Output**: Boolean indicating success
- **Success**: Returns True if task was deleted
- **Errors**:
  - ValueError if task with given ID does not exist

### Complete Task
- **Method**: complete_task(task_id: str) -> Task
- **Input**:
  - task_id (str, required): Unique identifier of the task
- **Output**: Updated Task object
- **Success**: Returns the Task object with completed status set to True
- **Errors**:
  - ValueError if task with given ID does not exist