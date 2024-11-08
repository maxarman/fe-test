# Profile Components

Your objective is to implement "commumication" between two **sibling components**—**Profile** and **EditProfile**—within `App.vue`

## Table of Contents

- [Profile Components](#profile-components)
  - [Table of Contents](#table-of-contents)
  - [Task Description](#task-description)
  - [Requirements](#requirements)
    - [Functional Requirements](#functional-requirements)

## Task Description

Create two sibling components, **Profile** and **EditProfile**, within `App.vue`. The **Profile** component should display user information, while the **EditProfile** component should allow editing of that information. Ensure that updates in one component are reflected in the other seamlessly.

## Requirements

### Functional Requirements

1. **Profile Component**
   - Display user information such as name, email
   - Reflect real-time updates when data is modified in the **EditProfile** component.

2. **EditProfile Component**
   - Provide a form to edit user information (e.g., name, email).

3. **Data Synchronization**
   - Ensure that changes made in **EditProfile** are immediately visible in **Profile**.
   - Handle state management effectively to maintain data consistency between components.

- Bonus: Validate input fields where applicable (e.g., proper email format).

