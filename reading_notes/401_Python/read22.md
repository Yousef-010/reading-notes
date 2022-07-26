# Readings: Django CRUD and Forms

> HTML forms
- in HTML, a form is a collection of elements inside `<form>...</form>` that allow a visitor to do things like enter text
- select options, manipulate objects or controls, and so on, and then send that information back to the server.
- the  `<input>` elements, a form must specify two things: 
  - where: the URL to which the data corresponding to the user’s input should be returned
  - how: the HTTP method the data should be returned by

> GET and POST
- GET and POST are the only HTTP methods to use when dealing with forms.
- Django’s login form is returned using the POST method, in which the browser bundles up the form data,
  - encodes it for transmission, sends it to the server, and then receives back its response.
- GET, by contrast, bundles the submitted data into a string, and uses this to compose a URL
  - The URL contains the address where the data must be sent, as well as the data keys and values.
- Any request that could be used to change the state of the system 
- for example, a request that makes changes in the database - should use POST. GET should be used only for requests that do not affect the state of the system.


> Django’s role in forms 
- Django’s form functionality can simplify and automate vast portions of this work,
- and can also do it more securely than most programmers would be able to do in code they wrote themselves.
- Django handles three distinct parts of the work involved in forms:
  - preparing and restructuring data to make it ready for rendering
  - creating HTML forms for the data
  - receiving and processing submitted forms and data from the client
- It is possible to write code that does all of this manually, but Django can take care of it all for you.


> Forms in Django 
- form class’s fields map to HTML form `<input>` elements.
- (A ModelForm maps a model class’s fields to HTML form `<input>` elements via a Form; 
- this is what the Django admin is based upon.)
- A form’s fields are themselves classes; they manage form data and perform validation when a form is submitted. 
  - DateField and a FileField handle very different kinds of data and have to do different things with it.
- A form field is represented to a user in the browser as an HTML “widget” - a piece of user interface machinery
  - Each field type has an appropriate default Widget class, but these can be overridden as required.


> Instantiating, processing, and rendering forms
- get hold of it in the view (fetch it from the database, for example)
- pass it to the template context
- expand it to HTML markup using template variables


> how to Build a form 
```
<form action="/your-name/" method="post">
    <label for="your_name">Your name: </label>
    <input id="your_name" type="text" name="your_name" value="{{ current_name }}">
    <input type="submit" value="OK">
</form>
```
- This tells the browser to return the form data to the URL /your-name/,
- using the POST method. It will display a text field, labeled “Your name:”, 
- and a button marked “OK”. If the template context contains a current_name variable,
- that will be used to pre-fill the your_name field.


> how to Build a form in Django
```
from django import forms
class NameForm(forms.Form):
    your_name = forms.CharField(label='Your name', max_length=100)
```
- A Form instance has an is_valid() method, which runs validation routines for all its fields. When this method is called, if all fields contain valid data, it will:
  - return True
  - place the form’s data in its cleaned_data attribute.


> The view 
- Form data sent back to a Django website is processed by a view, generally the same view which published the form. This allows us to reuse some of the same logic.
- example
```
from django.http import HttpResponseRedirect
from django.shortcuts import render
from .forms import NameForm
def get_name(request):
    # if this is a POST request we need to process the form data
    if request.method == 'POST':
        # create a form instance and populate it with data from the request:
        form = NameForm(request.POST)
        # check whether it's valid:
        if form.is_valid():
            # process the data in form.cleaned_data as required
            # ...
            # redirect to a new URL:
            return HttpResponseRedirect('/thanks/')
    # if a GET (or any other method) we'll create a blank form
    else:
        form = NameForm()
    return render(request, 'name.html', {'form': form})
```
- If we arrive at this view with a GET request
  - it will create an empty form instance and place it in the template context to be rendered. 
  - This is what we can expect to happen the first time we visit the URL.
- If the form is submitted using a POST request 
  - the view will once again create a form instance and populate it with data from the request: 
    - form = NameForm(request.POST) This is called “binding data to the form” (it is now a bound form).


> The template 
```
<form action="/your-name/" method="post">
    {{ form }}
    <input type="submit" value="Submit">
</form>
```
- All the form’s fields and their attributes will be unpacked into HTML markup from that {{ form }} by Django’s template language. 


> Bound and unbound form instances 
- An unbound form has no data associated with it. When rendered to the user, it will be empty or will contain default values.
- A bound form has submitted data, and hence can be used to tell if that data is valid. 
  - If an invalid bound form is rendered, it can include inline error messages telling the user what data to correct.



![image](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/admin_book_add.png)



![image](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_handling_-_standard.png)


> Resources 
- https://docs.djangoproject.com/en/4.0/topics/forms/ 
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Home_page
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Generic_views