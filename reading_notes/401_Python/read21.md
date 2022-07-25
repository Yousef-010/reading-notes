# Reading 21 Django Models


> The basic 
- Each model is a Python class that subclasses django.db.models.Model.
- Each attribute of the model represents a database field.
- With all of this, Django gives you an automatically-generated database-access API; see Making queries.


> Overview:
- Django web applications access and manage data through Python objects referred to as models. Models define the structure of stored data, 
- including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms
- The definition of the model is independent of the underlying database — you can choose one of several as part of your project settings. 
- Once you've chosen what database you want to use, you don't need to talk to it directly at all — you just write your model structure and other code, 
- and Django handles all the dirty work of communicating with the database for you.


> Designing the LocalLibrary models
- When designing your models it makes sense to have separate models for every "object" (a group of related information). In this case, the obvious objects are books, book instances, and authors.
- You might also want to use models to represent selection-list options (e.g. like a drop down list of choices)
- we need to think about the relationships. Django allows you to define relationships that are one to one (OneToOneField), one to many (ForeignKey) and many to many (ManyToManyField).

![image](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models/local_library_model_uml.svg)

- The diagram also shows the relationships between the models, including their multiplicities.
- The multiplicities are the numbers on the diagram showing the numbers (maximum and minimum) of each model that may be present in the relationship. 


> Model primer 
- This section provides a brief overview of how a model is defined and some of the more important fields and field arguments.
- Model definition 
  - Models are usually defined in an application's models.py file. 
  - They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata.
- Sample code
```
from django.db import models
from django.urls import reverse
class MyModelName(models.Model):
    """A typical class defining a model, derived from the Model class."""
    # Fields
    my_field_name = models.CharField(max_length=20, help_text='Enter field documentation')
    # …
    # Metadata
    class Meta:
        ordering = ['-my_field_name']
    # Methods
    def get_absolute_url(self):
        """Returns the URL to access a particular instance of MyModelName."""
        return reverse('model-detail-view', args=[str(self.id)])

    def __str__(self):
        """String for representing the MyModelName object (in Admin site etc.)."""
        return self.my_field_name

```

> COMMON FIELD ARGUMENTS 
- help_text: 
  - Provides a text label for HTML forms (e.g. in the admin site), as described above.
- verbose_name: 
  - A human-readable name for the field used in field labels. If not specified, Django will infer the default verbose name from the field name. 
- default:
  - The default value for the field. This can be a value or a callable object, in which case the object will be called every time a new record is created.
- null: 
  - If True, Django will store blank values as NULL in the database for fields where this is appropriate (a CharField will instead store an empty string). The default is False.
- blank: 
  - If True, the field is allowed to be blank in your forms. The default is False, which means that Django's form validation will force you to enter a value. This is often used with null=True , 
  - because if you're going to allow blank values, you also want the database to be able to represent them appropriately.
- choices: 
  - A group of choices for this field. If this is provided, 
  - the default corresponding form widget will be a select box with these choices instead of the standard text field.
  - primary_key: 
    - If True, sets the current field as the primary key for the model (A primary key is a special database column designated to uniquely identify all the different table records).
  

> COMMON FIELD TYPES 
- CharField
  - is used to define short-to-mid sized fixed-length strings. You must specify the max_length of the data to be stored.
- TextField
  - is used for large arbitrary-length strings.
  - You may specify a max_length for the field, but this is used only when the field is displayed in forms (it is not enforced at the database level).
- IntegerField
  - is a field for storing integer (whole number) values, and for validating entered values as integers in forms.


> Relationships 
- Many-to-one relationships
  - To define a many-to-one relationship, use django.db.models.ForeignKey. You use it just like any other Field type: by including it as a class attribute of your model.
  - ForeignKey requires a positional argument: the class to which the model is related.
```
from django.db import models
class Manufacturer(models.Model):
    # ...
    pass
class Car(models.Model):
    manufacturer = models.ForeignKey(Manufacturer, on_delete=models.CASCADE)
    # ...
```


- Many-to-many relationships
  - To define a many-to-many relationship, use ManyToManyField. You use it just like any other Field type: by including it as a class attribute of your model.
  - ManyToManyField requires a positional argument: the class to which the model is related.
```
from django.db import models
class Topping(models.Model):
    # ...
    pass
class Pizza(models.Model):
    # ...
    toppings = models.ManyToManyField(Topping)
```

- One-to-one relationships
  - To define a one-to-one relationship, use OneToOneField. You use it just like any other Field type: by including it as a class attribute of your model.
  - This is most useful on the primary key of an object when that object “extends” another object in some way.

> Model methods 
- Define custom methods on a model to add custom “row-level” functionality to your objects. 
- Whereas Manager methods are intended to do “table-wide” things, model methods should act on a particular model instance.
- This is a valuable technique for keeping business logic in one place – the model.
```
from django.db import models
class Person(models.Model):
    first_name = models.CharField(max_length=50)
    last_name = models.CharField(max_length=50)
    birth_date = models.DateField()
    def baby_boomer_status(self):
        "Returns the person's baby-boomer status."
        import datetime
        if self.birth_date < datetime.date(1945, 8, 1):
            return "Pre-boomer"
        elif self.birth_date < datetime.date(1965, 1, 1):
            return "Baby boomer"
        else:
            return "Post-boomer"
    @property
    def full_name(self):
        "Returns the person's full name."
        return '%s %s' % (self.first_name, self.last_name)
```

- __str__() 
  - A Python “magic method” that returns a string representation of any object
  - This is what Python and Django will use whenever a model instance needs to be coerced and displayed as a plain string.
  - Most notably, this happens when you display an object in an interactive console or in the admin.
  - You’ll always want to define this method; the default isn’t very helpful at all.

- get_absolute_url()
  - This tells Django how to calculate the URL for an object.
  - Django uses this in its admin interface, and any time it needs to figure out a URL for an object.



> Resources 
- https://docs.djangoproject.com/en/4.0/topics/db/models/ 
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site
- https://simpleisbetterthancomplex.com/series/2017/09/11/a-complete-beginners-guide-to-django-part-2.html
