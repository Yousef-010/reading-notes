# Read: Class 26

> Django
- What is Django? 
  - Django is a high-level Python web framework that enables rapid development of secure and maintainable websites
  - Built by experienced developers, Django takes care of much of the hassle of web development
  - so you can focus on writing your app without needing to reinvent the wheel.
  - It is free and open source, has a thriving and active community, great documentation
  - and many options for free and paid-for support.


- Why Django?
  - With Django, you can take web applications from concept to launch in a matter of hours.
  - Django takes care of much of the hassle of web development
    - you can focus on writing your app without needing to reinvent the wheel.
  - It’s free and open source.


> Characteristics of Django
- Ridiculously fast.
  - Django was designed to help developers take applications from concept to completion as quickly as possible.
- Fully loaded.
  - Django includes dozens of extras you can use to handle common web development tasks.
  - Django takes care of user authentication, content administration, site maps, RSS feeds,
  - and many more tasks — right out of the box.
- Reassuringly secure.
  - Django takes security seriously and helps developers avoid many common security mistakes, such as SQL injection,
  - cross-site scripting, cross-site request forgery and clickjacking.
  - Its user authentication system provides a secure way to manage user accounts and passwords.
- Exceedingly scalable.
  - Some of the busiest sites  use Django’s ability to quickly and flexibly scale to meet the heaviest traffic demands.
- Incredibly versatile.
  - Companies, organizations and governments have used Django to build all sorts of things
    - from content management systems to social networks to scientific computing platforms. 


> What does Django code look like?
  - In a traditional data-driven website, a web application waits for HTTP requests from the web browser 
  - When a request is received the application works out what is needed based on 
    - the URL and possibly information in POST data or GET data.
  - Depending on what is required it may then read or write information from 
    - a database or perform other tasks required to satisfy the request.
  - The application will then return a response to the web browser, 
  - often dynamically creating an HTML page for the browser to display
    - by inserting the retrieved data into placeholders in an HTML template.


![image here ](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction/basic-django.png)


> Quick install guide 
- Being a Python web framework, Django requires Python. 
- Python includes a lightweight database called SQLite so you won’t need to set up a database just yet.
- install the official Django
  - $ python -m pip install Django
- Install a version of Django provided by GitHub
  - $ git clone https://github.com/django/django.git
- Verifying 
  - import django
  - print(django.get_version())
  - 4.0

> How Django Works Behind the Scenes 
- Django follows the MVT design pattern (Model View Template).
  - Model - The data you want to present, usually data from a database.
  - View - A request handler that returns the relevant template and content - based on the request from the user.
  - Template - A text file (like an HTML file) containing the layout of the web page, with logic on how to display the data.
- Model
  - The model provides data from the database.
   In Django, the data is delivered as an Object Relational Mapping (ORM),
   which is a technique designed to make it easier to work with databases.
   The most common way to extract data from a database is SQL.
   One problem with SQL is that you have to have a pretty good understanding of the database structure to deal with it.
   Django, with ORM, makes it easier to communicate with the database, without having to write complex SQL statements
   The models are usually located in a file called models.py.

- View
  - A view is a function or method that takes http requests as arguments,
   imports the relevant model(s), and finds out what data to send to the template,
   and returns the final result. The views are usually located in a file called views.py.
- Template
  - A template is a file where you describe how the result should be represented.
  Templates are often .html files, with HTML code describing the layout of a web page,
  but it can also be in other file formats to present other results, but we will concentrate on .html files.
  Django uses standard HTML to describe the layout, but uses Django tags to add logic:

- URLs
  - Django also provide a way to navigate around the different pages in a website.
  When a user requests a URL, Django decides which view it will send it to.
  This is done in a file called urls.py.

    
> Resources 
- https://www.djangoproject.com/start/ 
- https://wsvincent.com/how-django-works-behind-the-scenes/ 
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Introduction
- https://docs.djangoproject.com/en/3.0/intro/tutorial01/
- https://docs.djangoproject.com/en/3.0/intro/tutorial02/
- https://www.w3schools.com/django/django_intro.php 
- https://djangoforbeginners.com/introduction/
