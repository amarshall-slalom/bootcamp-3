# UI Guidelines for TODO App

## Component Library

- Use Material UI (MUI) components for all form elements, buttons, dialogs, and lists.

## Color Palette

- Primary color: #1976d2 (blue)
- Secondary color: #ff9800 (orange)
- Background: #f5f5f5 (light gray)
- Text: #212121 (dark gray/black)
- Completed tasks: #9e9e9e (gray, with strikethrough)

## Button Styles

- Use contained buttons for primary actions (e.g., Add Task, Save)
- Use outlined buttons for secondary actions (e.g., Cancel, Edit)
- Buttons should have a minimum touch target of 48x48px

## Layout

- Responsive design: app must work on mobile, tablet, and desktop
- Use consistent spacing (8px grid)
- Tasks list should be easy to scan and interact with

## Accessibility

- All interactive elements must be keyboard accessible
- Use semantic HTML and ARIA attributes where appropriate
- Ensure sufficient color contrast (WCAG AA compliance)
- Provide visible focus indicators for all focusable elements

## Typography

- Use system font stack or Roboto (if using MUI)
- Headings: bold, clear hierarchy
- Task titles: medium weight, 16-18px
- Descriptions: regular weight, 14-16px

## Animations

- Use subtle transitions for adding, editing, and completing tasks
- Avoid excessive or distracting animations

## Icons

- Use Material Icons for actions (edit, delete, complete, etc.)

## Priority System

### Priority Badges

Priority badges indicate task urgency using color-coded chips:

- **P1 (High Priority)**: #d32f2f (red) - urgent tasks requiring immediate attention
- **P2 (Medium Priority)**: #ff9800 (orange) - important tasks with moderate urgency
- **P3 (Low Priority)**: #9e9e9e (gray) - routine tasks with no immediate deadline pressure

Badge styling:
- Use MUI `Chip` component with small size
- Display priority label text (P1, P2, or P3)
- Ensure WCAG AA contrast compliance
- Position badges in task list alongside due date badges

### Priority Selector (Form Control)

Priority selection uses button group or segmented control:

- **Unselected state**: #7a7a7a (gray) - indicates available but not chosen option
- **Selected state**: #07f2e6 (blue) - indicates currently active priority level
- Provide clear visual feedback on selection
- Default to P3 for new tasks
