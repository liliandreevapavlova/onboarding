## Project management app

### 1. Assignment Goals

The goal of this project is to show all accumulated knowledge in the last month.

Technologies:
- SCRUM
- GIT
- HTML & CSS
- JavaScript

### 2. Assignment Description

- General Requirements:
  - Create beautiful and responsive UI
  - Use semantic HTML
  - Use modules to split your application logic
  - Create several modules and use them in the routing
  - Use guards to prevent the user to access the routes
  - All of the data should be loaded from a web server
  - Each form should have validations and error handling
  - Your project should pass the default linting configuration without any errors
  - Your application should compile, work and produce an adequate result
  - Use Bitbucket and take advantage of the branches for writing your features.
  - Code Quality:
    - Meaningful methods and variable names;
    - Following JavaScripts code style guides and formatting;
    - Over/under used methods, classes, variables, data structures or code comments;
    - Adequate code reuse.
  - Unit test a few components and services

#### 2.1. Project Management Application Overview

The Project Management application manages the operations of an IT company. It brings visibility to an organization of multiple teams, working on multiple projects.

#### 2.2. Project Management Application Specifications

- The Project Management application is a platform for project management and time tracking.

- The system orchestrates the activities of multiple teams, each working on different projects.

- The system works with registered users. Each user is represented by a username, password, first name, last name and whether they have administrator access.

- A team is represented by a team name and team members.

- Each team can be assigned to a project.

- A project is represented by a name, description, owner and tasks - a list of tasks that need to be completed within the project scope. A project’s owner is the user that created the project. Although the project can have only one owner, it can have multiple teams assigned to it.

- A task is represented by a title, description, project (the project this task belongs to), assignee (the user that this task is assigned to), status (pending, in progress or completed) and a list of work logs (records, describing hours spent by users, working on the task).

- A work log is represented by a user (the user that worked on the task), time spent (the amount of hours spent working on the task for that day), date (the date when these hours were spent working on the task) and task (the task that these hours were spent on).

#### 2.3. Required Tasks

##### Authentication

- Story: 1. As a User I need to be able to log into the Project Management application with my username and password.
  If this is the first execution of the application and there are no users in the data store, I need to be able to log-in with the following user:

```
Username: admin
Password: adminpass
```

- Story: 2. As a User without administrative privileges my access to the Users & Teams Management View needs to be restricted.

##### Users Management

- Story: 3. As a User with administrative privileges I need to be able to **access** the Users Management View where I can list all users.
- Story: 4. As a User with administrative privileges I need to be able to **create** a user and persist the following information:

```
Username
Password
First Name
Last Name
```

All other information as **ID**, **Date of creation**, **ID of the creator**, **Date of last change**, **ID of the user that did the last change** are automatically set by the BE.

- Story: 5. As a User with administrative privileges I need to be able to **edit** a user by Id by providing the following information:

```
Username
Password
First Name
Last Name
```

- Story: 6. As a User with administrative privileges I need to be able to **delete** a user by ID.

##### Teams Management

- Story: 7. As a User with administrative privileges I need to be able to **access** the Teams Management View where I can list all teams.
- Story: 8. As a User with administrative privileges I need to be able to **create** a team and persist the following information:

```
Title
```

All other information as **ID**, **Date of creation**, **ID of the creator**, **Date of last change**, **ID of the user that did the last change** are automatically set by the BE

- Story: 9. As a User with administrative privileges I need to be able to **edit** a team by Id by providing the following information:

```
Title
```

- Story: 10. As a User with administrative privileges I need to be able to **delete** a team by Id
- Story: 11. As a User with administrative privileges I need to be able to **assign** users to a team.

##### Projects Management

- Story: 12. As a User I need to be able to **access** the Project Management View where I can access all Projects that are created by me or are assigned to teams where I’m a member.
- Story: 13. As a User I need to be able to **create** a Project and persist the following information:

```
Title
Description
```

All other information as **ID**, **Date of creation**, **ID of the creator**, **Date of last change**, **ID of the user that did the last change** are automatically set by the BE

- Story: 14. As a User I need to be able to **edit** a Project which I have created by Id by providing the following information:

```
Title
Description
```

- Story: 15. As a User I need to be able to **delete** a Project which I have created by Id.
- Story: 16. As a User I need to be able to **assign** Teams to Projects that I own.

NOTE: As a User in the Project Management View I should not be able to edit or delete projects that are not created by me, instead I should be able to access a detailed view of those projects where I’m able to browse through their tasks.

##### Task Management

- Story: 17. As a User I need to be able to **access** the Tasks Management View (Project Detailed Page) where I can access all Tasks from a single Project that is either created by me or is assigned to a Team that I’m a member of.
- Story: 18. As a User I need to be able to **create** a Task in a Project that I have created, and persist the following information:

```
Title
Description
Status (pending/inProgress/completed)
Assigne
```

All other information as **ID**, **Date of creation**, **ID of the creator**, **Date of last change**, **ID of the user that did the last change** are automatically set by the BE

- Story: 19. As a User I need to be able to **edit** a Task by Id, in the Projects that I have created, by providing the following information:

```
Title
Description
Status (pending/inProgress/completed)
Assignee
```

- Story: 20. As a User I need to be able to **delete** a Task by Id in the Projects that I have created.

:warning: NOTE: As a User I need to be able to access the Task Details View where I can log work to a Task

##### Work Log Management

- Story: 21. As a User I need to be able to **access** the Task Details View where I can access all Work Logs for this Task.
- Story: 22. As a User I need to be able to **create** a Work Log in a Task that is assigned to me, and persist the following information:

```
Time (the number of hours spent working on the Task for that day),
Date (the date when the time was spent on the Task) 
```

All other information as **ID**, **Id of the User** are automatically set by the BE.

- Story: 23. As a User I need to be able to **edit** a Work Log that I have created, by its Id, by providing the following information:

```
Time (the number of hours spent working on the Task for that day),
Date (the date when the time was spent on the Task)
```

- Story: 24. As a User I need to be able to **delete** a Work Log that I have created, by its Id.

:warning: NOTE: You should use the default input with type **date** for the Date log

#### 2.4. Extra Credit Task
- Story: 25. As a User I need to be able to see Dashboard with statistics about my projects:
    * Number of Projects that I am participating in or I created
    * Number of Tasks that are assigned to me 
    * Work in hours logged on tasks by me
    * Number of pending Tasks assigned to me   

#### 2.5 Design
[Project management application design](https://xd.adobe.com/view/55caebde-bffd-4e1b-79ad-3f9dec5567ab-23fb/grid)

### 3. Assignment Grading

Writing quality code that builds without warnings or errors, and then testing the resulting application and iterating until it functions properly is the goal.  

API
[API documantation](https://documenter.getpostman.com/view/9715100/SzezbraR?version=latest) TODO update to proper version

