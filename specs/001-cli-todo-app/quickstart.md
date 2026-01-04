# Quickstart Guide: CLI Todo App

## Prerequisites
- Python 3.12 or higher
- uv package manager

## Setup
1. Clone the repository
2. Navigate to the project directory
3. Install dependencies using uv:
   ```bash
   uv venv  # Create virtual environment
   uv pip install typer rich pytest  # Install required packages
   ```

## Running the Application
```bash
python -m src.cli.main
```

## Basic Usage
1. The application starts with an interactive menu
2. Choose from the available options:
   - Create Task: Add a new task with title, description, and priority
   - List Tasks: View all tasks with their status and priority
   - Update Task: Modify an existing task
   - Complete Task: Mark a task as completed
   - Delete Task: Remove a task from your list
   - Exit: Quit the application

## Example Task Creation
When creating a task, you'll be prompted to enter:
- Task title (required)
- Task description (optional)
- Priority level (high, medium, or low)

## Testing
Run the test suite with:
```bash
pytest
```

## Project Structure
- `src/models/task.py`: Task data model
- `src/services/task_service.py`: Task management logic
- `src/cli/main.py`: Main CLI interface
- `src/lib/storage.py`: File-based storage implementation
- `tests/`: All test files