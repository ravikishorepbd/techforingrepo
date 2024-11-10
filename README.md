# techforingrepo

# Techforing Project Management App

A project management application built with Django and Django REST Framework. This app allows users to manage projects, tasks, and comments, as well as to collaborate with team members.

## Table of Contents
- [Requirements](#requirements)
- [Installation](#installation)
- [Database Schema](#database-schema)
- [API Endpoints](#api-endpoints)
- [Authentication](#authentication)
- [Usage](#usage)

## Requirements

- Python 3.x
- Django 4.x
- Django REST Framework
- Django REST Framework Token Authentication

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/ravikishorepbd/techforingrepo.git
   cd techforingproject
   
## Database Schema
The database includes the following tables:

Users: Stores user details such as id, username, email, first_name, last_name, and date_joined.
Projects: Stores project details like id, name, description, owner, and created_at.
Project Members: Manages project members with fields like project_id, user_id, and role.
Tasks: Stores task details including id, title, description, status, priority, assigned_to, project, created_at, and due_date.
Comments: Stores comments on tasks with fields like id, content, user, task, and created_at.

## API Endpoints
The application provides the following API endpoints:

Users
Register: POST /api/users/register/ - Register a new user
Login: POST /api/users/login/ - Log in and retrieve an authentication token
User Details: GET /api/users/{id}/ - Retrieve details of a specific user
Update User: PUT/PATCH /api/users/{id}/ - Update user details
Delete User: DELETE /api/users/{id}/ - Delete a user account
Projects
List Projects: GET /api/projects/ - Retrieve a list of all projects
Create Project: POST /api/projects/ - Create a new project
Retrieve Project: GET /api/projects/{id}/ - Retrieve details of a specific project
Update Project: PUT/PATCH /api/projects/{id}/ - Update project details
Delete Project: DELETE /api/projects/{id}/ - Delete a project
Tasks
List Tasks: GET /api/projects/{project_id}/tasks/ - Retrieve a list of all tasks in a project
Create Task: POST /api/projects/{project_id}/tasks/ - Create a new task in a project
Retrieve Task: GET /api/tasks/{id}/ - Retrieve details of a specific task
Update Task: PUT/PATCH /api/tasks/{id}/ - Update task details
Delete Task: DELETE /api/tasks/{id}/ - Delete a task
Comments
List Comments: GET /api/tasks/{task_id}/comments/ - Retrieve a list of all comments on a task
Create Comment: POST /api/tasks/{task_id}/comments/ - Create a new comment on a task
Retrieve Comment: GET /api/comments/{id}/ - Retrieve details of a specific comment
Update Comment: PUT/PATCH /api/comments/{id}/ - Update comment details
Delete Comment: DELETE /api/comments/{id}/ - Delete a comment


## Authentication
This app uses Token Authentication for secure access to the API.

Obtain Token: After registering or logging in, a token is provided. This token is used for authenticating API requests.

Add Token to Headers: For each API request, add the token to the Authorization header in the format:

Authorization: Token your_token_here

curl -X GET http://127.0.0.1:8000/api/users/ -H "Authorization: Token your_token_here"

Generate Token Manually (Optional)
If you want to manually generate a token for a specific user, you can use Django's shell:

Open the Django shell:

bash
python manage.py shell
Create the token:



from django.contrib.auth.models import User
from rest_framework.authtoken.models import Token

 Replace 'ravikishorechavana' with the actual username
user = User.objects.get(username='ravikishorechavana')
token, created = Token.objects.get_or_create(user=user)
print(token.key)
The generated token will be printed. Use this token in the Authorization header for making API requests.

## Usage
Register a User: Use the /api/users/register/ endpoint to create a new user.
Authenticate: Log in at /api/users/login/ to receive a token for accessing other endpoints.
Create and Manage Projects and Tasks: Use the /api/projects/ and /api/projects/{project_id}/tasks/ endpoints to create and manage projects and their tasks.
Comment on Tasks: Use the /api/tasks/{task_id}/comments/ endpoint to add comments to tasks.

