# Product Requirements Document (PRD) - TODO App Enhancement: Due Dates, Priorities, and Filters

## 1. Overview

We are upgrading the basic TODO app to support due dates, priorities, and filters so users can better organize and manage their tasks. The current app only supports a title and completion status, which limits its practicality. This enhancement will enable users to prioritize work, track deadlines, and quickly view tasks based on urgency—all while maintaining simplicity and keeping the implementation teachable for bootcamp scenarios.

The upgrade will remain focused on local storage with no backend changes, ensuring a lean and accessible learning experience.

---

## 2. MVP Scope

### Core Features
- **Due Date Field**
  - Add optional due date to each task
  - Format: ISO `YYYY-MM-DD`
  - Invalid date values should be ignored (treated as absent)
  - Tasks can be created without a due date

- **Priority Levels**
  - Three priority levels: `P1` (high), `P2` (medium), `P3` (low)
  - Default priority: `P3`
  - Priority field is required (defaults to `P3` if not specified)
  - Visual representation using color-coded badges:
    - Red badge for P1
    - Orange badge for P2
    - Gray badge for P3

- **Filtering System**
  - Implement three filter tabs/views:
    - **All**: Display all tasks (including completed tasks)
    - **Today**: Display incomplete tasks with due date equal to today
    - **Overdue**: Display incomplete tasks with due date before today
  - Today and Overdue filters exclude completed tasks
  - All filter includes both completed and incomplete tasks
  - Quick tab switching between filter views

### Data Model Updates
- `title`: string, required (existing field)
- `completed`: boolean (existing field)
- `priority`: enum `"P1" | "P2" | "P3"`, default `"P3"` (new field)
- `dueDate`: string (ISO `YYYY-MM-DD`), optional (new field)

### Technical Constraints
- Maintain local storage implementation (localStorage)
- No backend API changes
- No external storage solutions
- Keep implementation simple and teachable

### User Experience
- Users can add/edit tasks with priority and due date
- Visual priority badges are immediately recognizable
- Filter tabs provide quick navigation between task views
- Completed tasks behavior respects filter context

---

## 3. Post-MVP Scope

### Visual Enhancements
- **Overdue Task Highlighting**
  - Overdue tasks (past due date) should be visually highlighted in red
  - Makes urgent items stand out prominently in the task list
  - Applies across all filter views where overdue tasks appear

### Advanced Sorting
- **Multi-level Sorting Logic**
  - Primary sort: Overdue status (overdue tasks first)
  - Secondary sort: Priority level (P1 → P2 → P3)
  - Tertiary sort: Due date (ascending - soonest first)
  - Final sort: Tasks without due dates appear last
  - This sorting applies to the task list display to optimize task management workflow

---

## 4. Out of Scope

The following features are explicitly excluded from both MVP and Post-MVP phases:

- **Notifications**
  - Push notifications
  - Email notifications
  - Browser notifications
  - Reminder alerts

- **Recurring Tasks**
  - Repeat schedules (daily, weekly, monthly)
  - Task templates
  - Automatic task duplication

- **Multi-user Support**
  - User accounts
  - Task sharing
  - Collaboration features
  - Permission management

- **Advanced Accessibility**
  - Keyboard navigation (beyond browser defaults)
  - Screen reader optimization
  - Custom accessibility features

- **External Storage**
  - Cloud synchronization
  - Database integration
  - Backend storage
  - Cross-device sync
  - API endpoints for task management

- **Additional Features**
  - Task categories/tags
  - Task descriptions beyond title
  - File attachments
  - Comments or notes
  - Task history/audit log
  - Search functionality
