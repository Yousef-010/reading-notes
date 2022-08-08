# Readings: Django REST Framework & Docker


> REST Framework 
- Django REST framework is a powerful and flexible toolkit for building Web APIs.
- reasons to know more about REST framework
  - reasonsThe Web browsable API is a huge usability win for your developers.
  - Authentication policies including packages for OAuth1a and OAuth2.
  - Serialization that supports both ORM and non-ORM data sources.
  - Customizable all the way down - just use regular function-based views if you don't need the more powerful features.
  - Extensive documentation, and great community support.
  - Used and trusted by internationally recognised companies including Mozilla, Red Hat, Heroku, and Eventbrite.


> Installation part 1 
- `pip install djangorestframework` 
- `pip install markdown`
- `pip install django-filter`
- **or clone this repo** `git clone https://github.com/encode/django-rest-framework`


> Installation part 2
- Add 'rest_framework' to your INSTALLED_APPS setting.
```
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```
- configure urls file
```
urlpatterns = [
    ...
    path('api-auth/', include('rest_framework.urls'))
]
```
- now open the API in your browser at `http://127.0.0.1:8000/` and view your new 'users' API.
- If you use the login control in the top right corner
- you'll also be able to add, create and delete users from the system.


> Serializers
- Serializers in Django REST Framework are responsible for converting objects into data types understandable by javascript and front-end frameworks.
- Serializers also provide deserialization, allowing parsed data to be converted back into complex types, after first validating the incoming data.
- The serializers in REST framework work very similarly to Django’s Form and ModelForm classes.
- The two major serializers that are most popularly used are ModelSerializer and HyperLinkedModelSerializer.
- Example
```
# import serializer from rest_framework
from rest_framework import serializers
# create a serializer
class CommentSerializer(serializers.Serializer):
    # initialize fields
    email = serializers.EmailField()
    content = serializers.CharField(max_length = 200)
    created = serializers.DateTimeField()
```


> ModelSerializer 
- The ModelSerializer class provides a shortcut that lets you automatically create a Serializer class with fields that correspond to the Model fields.
  - The ModelSerializer class is the same as a regular Serializer class, except that:
    - It will automatically generate a set of fields for you, based on the model.
    - It will automatically generate validators for the serializer, such as unique_together validators.
    - It includes simple default implementations of .create() and .update().


> HyperlinkedModelSerializer 
- The HyperlinkedModelSerializer class is similar to the ModelSerializer class except that it uses hyperlinks to represent relationships,
- rather than primary keys.
- Example
```
class SerializerName(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = ModelName
        fields = List of Fields
```


> Docker overview
- Docker is an open platform for developing, shipping, and running applications
- Docker enables you to separate your applications from your infrastructure so you can deliver software quickly
- With Docker, you can manage your infrastructure in the same ways you manage your applications


> The Docker platform
- Docker provides the ability to package and run an application in a loosely isolated environment called a container
- The isolation and security allows you to run many containers simultaneously on a given host.
- Containers are lightweight and contain everything needed to run the application, 
  - so you do not need to rely on what is currently installed on the host.


> Docker provides tooling and a platform to manage the lifecycle of your containers:
- Develop your application and its supporting components using containers.
- The container becomes the unit for distributing and testing your application.
- When you’re ready, deploy your application into your production environment, as a container or an orchestrated service.


> What can I use Docker for?
- Responsive deployment and scaling
- Running more workloads on the same hardware
- Others 
  - Your developers write code locally and share their work with their colleagues using Docker containers.
  - They use Docker to push their applications into a test environment and execute automated and manual tests.
  - When developers find bugs, they can fix them in the development environment and redeploy them to the test environment for testing and validation.
  - When testing is complete, getting the fix to the customer is as simple as pushing the updated image to the production environment.


> Docker architecture 

![image](https://docs.docker.com/engine/images/architecture.svg)


> Resources
- https://www.django-rest-framework.org/
- https://www.geeksforgeeks.org/serializers-django-rest-framework/
- https://docs.docker.com/get-started/overview/
- https://djangoforapis.com/library-website-and-api/
- https://wsvincent.com/beginners-guide-to-docker/