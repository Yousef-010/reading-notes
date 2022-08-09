# Readings: Permissions 


> Permissions 
- Permissions are used to grant or deny access for different classes of users to different parts of the API.
  - Authentication or identification by itself is not usually sufficient to gain access to information or code.
  - Permission checks are always run at the very start of the view, before any other code is allowed to proceed
  - Permission checks will typically use the authentication information in the 
  - `request.user` and `request.auth` properties to determine if the incoming request should be permitted.


> How permissions are determined
- always defined as a list of permission classes
- the types of exception `exceptions.PermissionDenied` or `exceptions.NotAuthenticated` 
- rules for permissions
  - The request was successfully authenticated, but permission was denied. — An HTTP 403 Forbidden response will be returned.
  - The request was not successfully authenticated, and the highest priority authentication class does not use `WWW-Authenticate` headers.
    - — An HTTP 403 Forbidden response will be returned.
  - The request was not successfully authenticated, and the highest priority authentication class does use `WWW-Authenticate` headers.
    - — An HTTP 401 Unauthorized response, with an appropriate `WWW-Authenticate` header will be returned.

> Object level permissions
- REST framework permissions also support object-level permissioning.
- usage 
  - to determine if a user should be allowed to act on a particular object


> Limitations of object level permissions
- may the generic views will not automatically apply object level permissions to each instance in a queryset when returning a list of objects.
- also want to filter the queryset appropriately,
  - to ensure that users only have visibility onto instances that they are permitted to view.
- because get_object() is not called 
  - object level permissions from the has_object_permission() method are not applied when creating objects


> Setting the permission policy
- default permission policy
```
REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticated',
    ]
}
```
- setting defaults to allowing unrestricted access: 
```
'DEFAULT_PERMISSION_CLASSES': [
   'rest_framework.permissions.AllowAny',
]
```


> API Reference 
- AllowAny
  - The `AllowAny` permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.
- IsAuthenticated
  - The `IsAuthenticated` permission class will deny permission to any unauthenticated user, and allow permission otherwise.
  - This permission is suitable if you want your API to only be accessible to registered users.
- IsAdminUser
  - The `IsAdminUser` permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.
  - This permission is suitable if you want your API to only be accessible to a subset of trusted administrators.
- IsAuthenticatedOrReadOnly
  - The `IsAuthenticatedOrReadOnly` will allow authenticated users to perform any request. 


> DjangoModelPermissions 
- `POST` requests require the user to have the `add` permission on the model.
- `PUT` and PATCH requests require the user to have the `change` permission on the model.
- `DELETE` requests require the user to have the `delete` permission on the model.


> Custom permissions 
- `.has_permission(self, request, view)`
- `.has_object_permission(self, request, view, obj)`
```
if request.method in permissions.SAFE_METHODS:
    # Check permissions for read-only request
else:
    # Check permissions for write request
```


> Third party packages 
- Third party packages
  - provides a way to define complex access rules in declarative policy classes that are attached to view sets or function-based views.
- Composed Permissions
  - provides a simple way to define complex and multi-depth (with logic operators) permission objects, using small and reusable components.
- REST Condition
  - it is another extension for building complex permissions in a simple and convenient way.
- DRY Rest Permissions
  - provides the ability to define different permissions for individual default and custom actions.
- Django Rest Framework Roles
  - The Django Rest Framework Roles package makes it easier to parameterize your API over multiple types of users.
- Django REST Framework API Key
  - The Django REST Framework API Key package provides permissions classes, models and helpers to add API key authorization to your API
- Django Rest Framework Role Filters
  - The Django Rest Framework Role Filters package provides simple filtering over multiple types of roles.
- Django Rest Framework PSQ
  - it  is an extension that gives support for having action-based permission_classes, serializer_class, and queryset dependent on permission-based rules. 


> Resources 
- https://www.django-rest-framework.org/api-guide/permissions/#django-rest-framework-role-filters
- https://codefellows.github.io/common_curriculum/prep_work/SQL
- https://www.cdrf.co/
- https://www.django-rest-framework.org/api-guide/generic-views/