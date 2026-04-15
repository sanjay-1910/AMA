## 1. What is Middleware?

Middleware is a layer in Django that processes requests and responses globally before they reach the view or before they are returned to the user.

It acts like a **bridge between the request and the response**.

### How it works
Request → Middleware → View → Middleware → Response

### Uses of Middleware
- Authentication
- Security
- Logging
- Session management
- CSRF protection

### Examples of Django Middleware
- `AuthenticationMiddleware` → identifies the logged-in user
- `SessionMiddleware` → manages sessions
- `CsrfViewMiddleware` → protects against CSRF attacks
- `SecurityMiddleware` → adds security headers

---

# 2. Syntax to Load Static Images in Django

First load the static files in the template.

```html
{% load static %}

```

Then use the static tag.

```html
<img src="{% static 'images/photo.png' %}" alt="image">

```

----------

# 3. What is ORM?

ORM stands for **Object Relational Mapping**.

It allows developers to interact with the database using **Python code instead of writing SQL queries manually**.

Django ORM converts Python code into SQL queries automatically.

### Example

Python ORM query:

```python
User.objects.all()

```

Converted SQL:

```sql
SELECT * FROM user;

```

### Benefits

-   No need to write raw SQL
    
-   Safer (prevents SQL injection)
    
-   Easy database operations
    

----------

# 4. Explain Liskov Substitution Principle

The **Liskov Substitution Principle (LSP)** is one of the **SOLID principles of object-oriented programming**.

It states that:

> Objects of a child class should be able to replace objects of the parent class without breaking the program.

### Example

Bad Example

If a `Bird` class has a method `fly()` and a `Penguin` inherits from `Bird` but cannot fly, then it violates LSP.

Good Design

Separate the flying behavior so that only flying birds implement it.

----------

# 5. Difference Between urls.py in App Level and Project Level

### Project Level `urls.py`

This file handles the **main URL routing of the entire Django project**.

It usually includes URLs from different apps.

Example:

```python
from django.urls import path, include

urlpatterns = [
    path("admin/", admin.site.urls),
    path("products/", include("products.urls")),
]

```

### App Level `urls.py`

This file contains **URL routes specific to that app only**.

Example:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.home),
    path("details/", views.details),
]

```
----------

# 6. Difference Between null and blank

Both are used in Django model fields.

### `null=True`

-   Stored at **database level**
    
-   Allows the database column to store **NULL values**
    

### `blank=True`

-   Used at **form validation level**
    
-   Allows the field to be **empty in forms**
    

### Example

```python
name = models.CharField(max_length=100, blank=True)
age = models.IntegerField(null=True)

```

----------

# 7. What are Forms in Django?

Forms in Django are used to **collect user input from the browser and validate it**.

They help process data safely.

### Types of Forms

1.  **Forms.Form**
    
    -   Manual form creation
        
2.  **ModelForm**
    
    -   Automatically creates forms from models
        

### Example

```python
class ContactForm(forms.Form):
    name = forms.CharField()
    email = forms.EmailField()

```

----------

# 8. What is QuerySet?

A QuerySet is a **collection of objects retrieved from the database**.

It represents the result of a database query.

### Example

```python
Product.objects.all()

```

This returns a QuerySet containing all products.

### Common QuerySet Operations

```python
Product.objects.filter(price=100)
Product.objects.get(id=1)
```

----------

# 9. How Do You Implement Different Settings for Local and Production?

You can create **multiple settings files**.

### Example Structure

```
settings/
    base.py
    local.py
    production.py

```

### base.py

Common settings.

### local.py

Development settings.

```python
DEBUG = True

```

### production.py

```python
DEBUG = False
ALLOWED_HOSTS = ["yourdomain.com"]

```

Run server with:

```
python manage.py runserver --settings=project.settings.local

```

----------

# 10. What Are ACID Properties in SQL?

ACID ensures reliable database transactions.

### A – Atomicity

Transaction happens completely or not at all.

### C – Consistency

Database remains valid before and after a transaction.

### I – Isolation

Transactions do not affect each other.

### D – Durability

Once data is committed, it is permanently saved.

----------

# 11. What is Django Template Language (DTL)?

DTL is the templating system used by Django to generate dynamic HTML pages.

It allows embedding Python-like logic inside HTML.

### Example

```html
<h1>{{ user.username }}</h1>

```

### Common DTL Tags

Loop

```html
{% for product in products %}
    {{ product.name }}
{% endfor %}

```

Condition

```html
{% if user.is_authenticated %}
    Welcome
{% endif %}

```

----------

# 12. How to Load Environment Variables (.env file)

We usually use **python-dotenv** or **django-environ**.

### Install

```
pip install python-dotenv

```

### Example

```python
from dotenv import load_dotenv
import os

load_dotenv()

SECRET_KEY = os.getenv("SECRET_KEY")

```

----------

# 13. Explain Validators

Validators are used to **validate data before saving it to the database**.

They ensure the data meets certain conditions.

### Example

```python
from django.core.validators import MinValueValidator

age = models.IntegerField(validators=[MinValueValidator(18)])

```

This ensures age must be at least 18.

----------

# 14. What is .venv?

`.venv` is a **virtual environment folder**.

It contains a separate Python environment with installed packages for the project.

### Why it is used

-   Isolates dependencies
    
-   Prevents version conflicts
    
-   Keeps project packages separate from system Python
    

### Create Virtual Environment

```
python -m venv .venv

```

----------

## 15. Which Field is Used to Store Images in Django?

In Django, images can be stored mainly using **ImageField**.  
Another possible way is using **BinaryField**, but it is rarely used in real projects.

---

### 1. Using ImageField (Most Common Method)

**ImageField** is the standard field provided by Django to handle image uploads.

Example:

```python
image = models.ImageField(upload_to="products/")

```

**Explanation**

-   `upload_to="products/"` means uploaded images will be stored in the `products` folder inside the media directory.
    
-   The **actual image file is stored in the file system**, not inside the database.
    
-   The **database only stores the path of the image**.
    

Example stored in database:

```
products/laptop.png

```

**Requirement**

Django requires the **Pillow** library to process images.

Install it using:

```
pip install pillow

```

**Why ImageField is preferred**

-   Keeps the database size small
    
-   Faster database queries
    
-   Easier to manage and serve images
    

----------

### 2. Using BinaryField (Storing Image in Database)

Django also provides **BinaryField**, which allows storing **raw binary data directly inside the database**.

Example:

```python
class Product(models.Model):
    name = models.CharField(max_length=100)
    image = models.BinaryField()

```

To save an image:

```python
with open("image.png", "rb") as f:
    img_data = f.read()

Product.objects.create(
    name="Laptop",
    image=img_data
)

```

**Explanation**

-   The image file is converted into **binary data**
    
-   The **entire image is stored inside the database column**
    

----------
