# Calorie Co App Development Project Plan

## Week 1: Project Setup and Initial Exploration

### Master Basic Concepts:
- **Python Basics:**
  - Dive into Python's syntax and foundational programming concepts. Engage with tutorials or exercises to strengthen your grasp on Python. Resources like Python's official documentation or Codecademy are excellent starting points.

- **Introduction to Django:**
  - Explore Django's core philosophies, especially the DRY (Don't Repeat Yourself) principle and the concept of "convention over configuration."
  - Learn about Django's MTV (Model-Template-View) architecture, which is fundamental for web development with Django.
  - Follow Django's official tutorial to create your first project and app, defining models, setting up the admin interface, and creating simple views and templates.

- **REST API Fundamentals:**
  - Understand the basics of what an API (Application Programming Interface) is and its role in software communication.
  - Learn about REST (Representational State Transfer) principles and how RESTful APIs use HTTP methods for operations.
  - Explore how Django can be extended with Django REST Framework (DRF) to build RESTful APIs, focusing on serializing data and creating API views.

- **Version Control with Git:**
  - Grasp the importance of version control in software development projects.
  - Familiarize yourself with basic Git commands (`git init`, `git clone`, `git add`, `git commit`, `git push`, `git pull`) and the concepts of branching and merging.
  - Practice using GitHub or other Git hosting services for code collaboration and version management.

### Set Up Your Development Environment:
- **Install Python and Django:**
  - Ensure Python is correctly installed on your computer. Use Python's package manager, pip, to install Django within a virtual environment to manage project dependencies effectively.

- **Database Setup:**
  - Choose and install a database system (MySQL or PostgreSQL). Configure your Django project's `settings.py` to connect to your database.

- **Virtual Environment:**
  - Learn to create and manage a virtual environment using Python's `venv` module for your project. This isolates your project's dependencies and is essential for a clean development environment.

- **Text Editor or IDE:**
  - Select a text editor or Integrated Development Environment (IDE) that you are comfortable with. Visual Studio Code, PyCharm, and Atom are popular choices offering features like syntax highlighting, code completion, and debugging tools.

- **Command Line Basics:**
  - If new to the command line, familiarize yourself with basic commands for navigating directories, running Python and Django commands, and interacting with Git. This skill is crucial for efficient development.

- **Initial Project Steps:**
  - Start your Django project by running `django-admin startproject myproject`. Then, test your setup by launching the development server with `python manage.py runserver` and visiting the provided local server address in your browser.

### Database Setup with MySQL/MariaDB:
- **Choosing MySQL/MariaDB:** For this project, we'll use MySQL or MariaDB as our database. Both are powerful, open-source database systems compatible with Django. MariaDB is a community-developed fork of MySQL, ensuring excellent compatibility.

- **Installation:**
  - **MySQL:** Install MySQL from the official website or use your operating system's package manager. For Windows, you can use the MySQL Installer; for macOS and Linux, use Homebrew or `apt-get` respectively.
  - **MariaDB:** Similarly, install MariaDB directly from the MariaDB repository or via your OS's package manager.

- **Database Configuration:**
  - Once installed, create a new database for your Django project. You can use graphical tools like MySQL Workbench or command-line instructions:
    ```
    CREATE DATABASE calorie_co CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
    ```
  - Create a user and grant it all privileges on your new database. This is crucial for ensuring Django can interact with your database securely.
    ```
    CREATE USER 'calorie_co_user'@'localhost' IDENTIFIED BY 'your_password';
    GRANT ALL PRIVILEGES ON calorie_co.* TO 'calorie_co_user'@'localhost';
    FLUSH PRIVILEGES;
    ```

- **Configure Django to Use MySQL/MariaDB:**
  - In your Django project's `settings.py`, configure the `DATABASES` setting to use MySQL/MariaDB by specifying the `ENGINE`, `NAME`, `USER`, `PASSWORD`, `HOST`, and `PORT`:
    ```python
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'calorie_co',
            'USER': 'calorie_co_user',
            'PASSWORD': 'your_password',
            'HOST': 'localhost',  # Or the IP address of your database server
            'PORT': '3306',  # Default MySQL/MariaDB port
        }
    }
    ```
  - Ensure the `mysqlclient` Python package is installed in your virtual environment to enable Django to communicate with MySQL/MariaDB:
    ```
    pip install mysqlclient
    ```

### Folder Structure
A Django project structured for deployment and development typically includes the following folder structure:
```
myproject/
│
├── myproject/          # Django project directory
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py     # Django settings
│   ├── urls.py         # Project URLs
│   └── wsgi.py
│
├── app/                # Django app directory
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py        # Admin site configuration
│   ├── apps.py         # App configuration
│   ├── models.py       # Database models
│   ├── tests.py        # Test cases
│   ├── urls.py         # App URLs
│   └── views.py        # View functions
│
├── templates/          # HTML templates
├── static/             # Static files like CSS, JavaScript, images
├── media/              # User-uploaded content
├── Dockerfile          # Docker configuration file
├── docker-compose.yml  # Docker compose file for service definitions
├── requirements.txt    # Project dependencies
└── manage.py           # Django command line utility
```

This structure separates concerns within your project, making it easier to manage development, testing, and deployment phases.


This week is all about laying the groundwork for your project. By the end, you'll have a solid understanding of the tools and technologies you'll be using and will be ready to start developing your application.


## Week 2: User Authentication and Database Models

- [ ] **Django Project and App Setup:**
  - Begin by setting up your Django project and creating a dedicated app for the calorie tracking functionality. This is where your project starts taking shape.

- [ ] **Database Configuration:**
  - **Learn and Implement Django Models:**
    - Understand that models in Django define the structure of your database. For instance, a `CalorieEntry` model could have fields such as `user`, `date`, `calories`, and `description`.
    - Here's an example to define a `CalorieEntry` model:
      ```python
      from django.db import models
      from django.contrib.auth.models import User

      class CalorieEntry(models.Model):
          user = models.ForeignKey(User, on_delete=models.CASCADE)
          date = models.DateField(auto_now_add=True)
          calories = models.IntegerField()
          description = models.TextField(blank=True)

          def __str__(self):
              return f"{self.user.username} - {self.date} - {self.calories} calories"
      ```
  - **Set Up and Configure Your Database:**
    - Adjust the `settings.py` file in your Django project to configure your database settings. This involves selecting a database engine (e.g., PostgreSQL) and specifying connection parameters.
    - For PostgreSQL, you might have a setup like this:
      ```python
      DATABASES = {
          'default': {
              'ENGINE': 'django.db.backends.postgresql',
              'NAME': 'calorie_co',
              'USER': 'mydatabaseuser',
              'PASSWORD': 'mypassword',
              'HOST': 'localhost',
              'PORT': '',
          }
      }
      ```
    - Don't forget to run migrations to create your database schema.

- [ ] **Implement User Authentication:**
  - **Set Up Registration and Login:**
    - Utilize Django's built-in forms and views to enable user registration and login. This allows users to create accounts and access their information securely.
    - For registration, consider using `UserCreationForm` and a view like this:
      ```python
      from django.contrib.auth.forms import UserCreationForm
      from django.urls import reverse_lazy
      from django.views import generic

      class SignUpView(generic.CreateView):
          form_class = UserCreationForm
          success_url = reverse_lazy('login')
          template_name = 'signup.html'
      ```
  - **Configure Login and Logout Paths:**
    - Set up URL patterns in `urls.py` to utilize Django's views for login and logout functionalities. Here’s how you might configure them:
      ```python
      from django.contrib.auth.views import LoginView, LogoutView
      from django.urls import path

      urlpatterns = [
          path('login/', LoginView.as_view(), name='login'),
          path('logout/', LogoutView.as_view(), name='logout'),
      ]
      ```
  - **Integrate JWT for Secure API Access:**
    - Install `djangorestframework-simplejwt` for JWT authentication in your REST API. This adds an extra layer of security for API requests.
    - Configure JWT authentication in the DRF settings and set up endpoints for obtaining and refreshing tokens. Testing these endpoints with tools like Postman ensures your API is secure.

This week focuses on setting up user authentication and database models, foundational aspects that will drive your application's functionality and security.



## Week 3: Core Functionality and REST API Development

- [ ] **Design and Implement Calorie Tracking Models:**
  - Create a `CalorieEntry` model with fields for user, date, calories, and description. Check out the Django documentation for guidance on model relationships, like ForeignKey with the User model.
  - Make sure to register your models with the Django admin. This allows you to easily manage entries during testing.

- [ ] **Implement Calorie Entry and Daily Total Calculation:**
  - Implement forms for user input on calorie entries. Dive into Django forms to capture user data efficiently.
  - Create views to process form submissions and to display calorie data. Whether you choose function-based or class-based views, here's a simple structure to follow:
      ```
      def calorie_entry_submit(request):
          if request.method == 'POST':
              form = CalorieEntryForm(request.POST)
              if form.is_valid():
                  form.save()
                  return redirect('success_page')
          else:
              form = CalorieEntryForm()
          return render(request, 'entry_form.html', {'form': form})
      ```
  - Calculate and display daily totals by aggregating calorie entries by date. Explore Django's Sum function for this task.

- [ ] **Develop REST API Endpoints:**
  - Understand the role of serializers by creating a `CalorieEntrySerializer` for converting model instances to JSON and back.
  - Configure viewsets or API views for CRUD operations on calorie entries, simplifying URL management with Django REST Framework's routers. Here's an example to guide you:
      ```
      class CalorieEntryViewSet(viewsets.ModelViewSet):
          queryset = CalorieEntry.objects.all()
          serializer_class = CalorieEntrySerializer
      ```
  - Ensure your API endpoints are secure. Integrate JWT authentication to protect user data, allowing access only to their entries.

- [ ] **Testing API Endpoints:**
  - Manually test your API endpoints with tools like Postman or curl. This step is crucial for verifying the functionality of your API.
  - Start writing tests for your API views to confirm they work as expected. Testing early and often helps catch issues before they become problematic.

## Week 4: Testing and Basic Frontend Development

### Frontend Development for Basic Functionality:
- **Implement Basic Frontend Features:** 
  - Use Django templates to create forms for user registration, login, and calorie entry. 
  - Example for a calorie entry form in HTML:
    ```html
    <form method="post">
      {% csrf_token %}
      <!-- Include form fields here -->
      <input type="number" name="calories" placeholder="Calories">
      <input type="submit" value="Submit">
    </form>
    ```

### Comprehensive Backend Testing:
- **Unit Test Your Models and Views:**
  - For models, test data creation and expected behaviors.
    ```python
    from django.test import TestCase
    from .models import CalorieEntry

    class CalorieEntryModelTest(TestCase):
        def test_create_calorie_entry(self):
            # Create a calorie entry and verify it's saved correctly
            entry = CalorieEntry.objects.create(calories=200)
            self.assertEqual(entry.calories, 200)
    ```
  - For views, ensure they return the correct HTTP status codes and templates.
    ```python
    class CalorieEntryViewTest(TestCase):
        def test_calorie_entry_view(self):
            response = self.client.get('/calorie-entry/')
            self.assertEqual(response.status_code, 200)
            self.assertTemplateUsed(response, 'calorie_entry.html')
    ```

- **Test REST API Endpoints:**
  - Verify API behavior with DRF's `APITestCase`.
    ```python
    from rest_framework.test import APITestCase
    from rest_framework import status

    class CalorieEntryAPITest(APITestCase):
        def test_create_entry(self):
            url = '/api/calorie-entries/'
            data = {'calories': 500}
            response = self.client.post(url, data, format='json')
            self.assertEqual(response.status_code, status.HTTP_201_CREATED)
    ```

- **Perform Integration Testing:**
  - Test the flow of your application from end to end.
    ```python
    class UserFlowTest(TestCase):
        def test_user_registration_to_calorie_entry(self):
            # Test the complete user flow from registration to submitting a calorie entry
            self.client.post('/register/', {'username': 'testuser', 'password': 'password'})
            self.client.login(username='testuser', password='password')
            self.client.post('/calorie-entry/', {'calories': 200})
            # Check the calorie entry was created successfully
    ```

### Achieve High Test Coverage:
- **Use Coverage Tools:**
  - Install the coverage tool in your virtual environment using pip: `pip install coverage`.
  - Run coverage analysis to measure how much of your code is executed while running tests. Use the command: `coverage run manage.py test`.
  - After running your tests with coverage, generate a report to see your test coverage percentage. Use the command: `coverage report`.
  - Aim for a high percentage of coverage to ensure most of your code is tested, which helps in maintaining a reliable and bug-free application.

This detailed plan for Week 4 provides you with structured guidance on developing basic frontend features and conducting comprehensive testing, including practical pseudocode examples to help understand the implementation.


## Week 5: Deployment and Documentation

### Deployment:
- **Heroku Deployment:**
  - Install the Heroku CLI and log in.
  - Prepare your Django app with `Procfile`, `requirements.txt`, and `runtime.txt`.
  - Create a new app with `heroku create`.
  - Deploy using `git push heroku master`.
  - Run migrations with `heroku run python manage.py migrate`.

- **AWS Deployment:**
  - **EC2 for Running Your Server:**
    - Launch an EC2 instance using the AWS Management Console. Select an AMI (Amazon Machine Image) that suits your project's needs.
    - SSH into your instance after setup and install necessary software (e.g., Python, Django).
  - **RDS for Database:**
    - Create an RDS instance for your database. Choose the same database engine as your development environment (e.g., MySQL, PostgreSQL).
    - Configure your Django project's `settings.py` to connect to your RDS database.
  - **S3 for Static and Media Files:**
    - Set up an S3 bucket for storing static and media files.
    - Configure Django to use S3 for file storage with packages like `django-storages` and `boto3`.
  - **Deploy Your Application:**
    - Transfer your project files to your EC2 instance using SCP or a Git repository.
    - Set up a web server like Gunicorn to serve your Django app and Nginx as a reverse proxy to handle HTTP requests.

### Documentation and Cleanup:
- **Document Your Project:**
  - Use Swagger or DRF's schema generation for API documentation. Include setup instructions, dependencies, and usage examples in a README file.
- **Refine Your Codebase:**
  - Ensure code consistency, remove unused code, and apply best practices.
- **Final Project Review:**
  - Review your project with peers or mentors for feedback and potential improvements.

### Running Your Project Locally:
- **Local Environment Setup:**
  - Ensure Python and Django are installed.
  - Install dependencies from `requirements.txt` using `pip install -r requirements.txt`.
  - Run migrations with `python manage.py migrate` to set up your database schema.
  - Start the development server using `python manage.py runserver` and navigate to `http://localhost:8000` to view your project.

### Dockerizing Your Django Project:
- **Create a Dockerfile:**
  - Start by creating a `Dockerfile` in your project root:
    ```Dockerfile
    FROM python:3.8
    ENV PYTHONUNBUFFERED 1
    RUN mkdir /code
    WORKDIR /code
    ADD requirements.txt /code/
    RUN pip install -r requirements.txt
    ADD . /code/
    ```
  - This Dockerfile sets up a Python environment, installs your project's dependencies, and adds your project to the container.

- **Define Services in docker-compose.yml:**
  - Create a `docker-compose.yml` file to define your Django app and any other services (like a database):
    ```yaml
    version: '3'
    services:
      db:
        image: postgres
        environment:
          POSTGRES_DB: dbname
          POSTGRES_USER: user
          POSTGRES_PASSWORD: password
      web:
        build: .
        command: python manage.py runserver 0.0.0.0:8000
        volumes:
          - .:/code
        ports:
          - "8000:8000"
        depends_on:
          - db
    ```
  - This configuration sets up a Django app (`web`) and a PostgreSQL database (`db`) service.

- **Build and Run Your Container:**
  - Run `docker-compose up --build` to build your image and start your containers.
  - Access your app at `http://localhost:8000`.


This detailed Week 5 plan guides you through deploying your Django project on Heroku and AWS, ensuring you understand the steps involved in making your application live. Additionally, the focus on documentation and code refinement prepares your project for future development and collaboration.
