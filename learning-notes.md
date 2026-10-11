## Django Project vs Django App

### Django Project

The overall application configuration. It contains settings, URLs, database configuration, and other project-level configuration.

### Django App

A specific feature or section of a Django project. An app contains related models, views, URLs, etc.

Example:
it
TaskFlow (Project)
↓
tasks (App)
↓
Task-related functionality

## Django App

A Django app is a module that handles a specific area of functionality within a Django project.

**Command to create an app:**
`python manage.py startapp tasks`

**Important files:**

- `models.py`: Defines database models.
- `views.py`: Handles requests and returns responses.
- `admin.py`: Registers models for the Django admin interface.
- `apps.py`: Contains app configuration.
- `tests.py`: Contains automated tests.
- `migrations/`: Stores database schema change instructions.

**INSTALLED_APPS:** A setting in `settings.py` that tells Django which apps are enabled in the project. A newly created app should be registered here.

## Django Models and Migrations

**Model:** A Python class that defines the structure of data stored in a database.

**ORM (Object-Relational Mapper):** Allows us to interact with database records using Python objects instead of writing SQL for every operation.

**Fields:** Define what data a model stores. Examples include `CharField`, `TextField`, and `DateTimeField`.

**`__str__()`:** Defines a readable text representation of a model object.

**Migrations:** Track changes to the database schema.

- `python manage.py makemigrations tasks` generates migration instructions for the `tasks` app.
- `python manage.py migrate` applies pending migrations to the database.

**Remember:** `makemigrations` generates the instructions; `migrate` applies them.

## Django Admin

Django Admin is a built-in web interface for managing database records.

**`admin.py`:** Used to register models with Django Admin.

**Example:**

```python
from django.contrib import admin
from .models import Task

admin.site.register(Task)
```

**Create a superuser:**
`python manage.py createsuperuser`

**Purpose:** Admin allows developers to create, view, update, and delete records through a browser without building a custom interface.

**Important:** Registering a model makes it available in Django Admin; it does not create the database table. Migrations handle database schema changes.

## APIs and Django REST Framework

**API:** A way for two software systems to communicate. Our React frontend will request data from Django through an API.

**JSON:** A data format used to exchange structured information between the frontend and backend.

**Django REST Framework (DRF):** A toolkit for building APIs with Django.

**Serializer:** Converts Django model instances into JSON-compatible data and validates incoming data.

**ModelSerializer:** A DRF serializer that automatically derives fields and common validation rules from a Django model.

**Example:**

```python
from rest_framework import serializers
from .models import Task

class TaskSerializer(serializers.ModelSerializer):
    class Meta:
        model = Task
        fields = "__all__"
```

**Remember:** A model defines the data structure, a serializer handles its representation and validation, and a view handles the request/response logic.
