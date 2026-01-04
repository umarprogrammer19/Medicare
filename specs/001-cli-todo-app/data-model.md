# Data Model: CLI Todo App

## Task Entity

### Fields
- **id**: str (UUID) - Unique identifier for the task
- **title**: str - Title of the task (required, max 200 characters)
- **description**: str - Optional description of the task (max 1000 characters)
- **priority**: str - Priority level (values: "high", "medium", "low")
- **completed**: bool - Completion status (default: False)
- **created_at**: datetime - Timestamp when task was created
- **updated_at**: datetime - Timestamp when task was last updated

### Validation Rules
- Title must not be empty
- Title must be 200 characters or less
- Description can be empty but limited to 1000 characters if provided
- Priority must be one of: "high", "medium", "low"
- completed defaults to False when creating new tasks

### State Transitions
- **Created**: New task with completed=False
- **Updated**: Task details modified (title, description, priority, or completion status)
- **Completed**: Task completion status changed from False to True
- **Deleted**: Task removed from the system

## Task List Entity

### Fields
- **tasks**: List[Task] - Collection of Task entities
- **total_count**: int - Total number of tasks in the list
- **completed_count**: int - Number of completed tasks
- **pending_count**: int - Number of pending tasks

### Relationships
- Contains multiple Task entities
- Provides filtering and sorting capabilities for tasks

### Operations
- Add new Task
- Remove Task by ID
- Update Task by ID
- Filter by completion status
- Filter by priority level
- Sort by creation date, priority, or title