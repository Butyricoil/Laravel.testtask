### Task 1: CRUD with Relationships

Create a simple application for managing projects and tasks.

**Requirements:**

- **Tables:** `projects` and `tasks`
- One project can have many tasks.
- Each task has the following fields:
  - `title`
  - `status`
  - `deadline`
- Implement full **CRUD** (Create, Read, Update, Delete) functionality.
- When a project is deleted, all its related tasks must also be deleted (using **cascade delete**).
