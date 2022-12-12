# Read 26: Permissions & Postgresql

## DRF Permissions:[source](https://www.django-rest-framework.org/api-guide/permissions/)

### DRF Permissions
In DRF, permissions, along with authentication and throttling, are used to grant or deny access for different classes of users to different parts of an API.

Authentication and authorization work hand in hand. Authentication is always executed before authorization.

While authentication is the process of checking a user's identity (the user the request came from, the token that it was signed with), authorization is a process of checking if the request user has the necessary permissions for executing the request (are they a super user, are they the creators of the object).

The authorization process in DRF is covered by permissions.


### View Permissions:

**has two methods that check for permissions:**

1. `check_permissions` checks if the request should be permitted based on request data
2. c`heck_object_permissions` checks if the request should be permitted based on the combination of the request and object data
```
class APIView(View):
    # other methods
    def check_permissions(self, request):
        """
        Check if the request should be permitted.
        Raises an appropriate exception if the request is not permitted.
        """
        for permission in self.get_permissions():
            if not permission.has_permission(request, self):
                self.permission_denied(
                    request,
                    message=getattr(permission, 'message', None),
                    code=getattr(permission, 'code', None)
                )

    def check_object_permissions(self, request, obj):
        """
        Check if the request should be permitted for a given object.
        Raises an appropriate exception if the request is not permitted.
        """
        for permission in self.get_permissions():
            if not permission.has_object_permission(request, self, obj):
                self.permission_denied(
                    request,
                    message=getattr(permission, 'message', None),
                    code=getattr(permission, 'code', None)
                )
```

### Permission classes

**Permissions in DRF are defined as a list of permission classes. You can either create your own or use one of the seven built-in classes. All permission classes, either custom or built-in, extend from the BasePermission class:**

``` 
class BasePermission(metaclass=BasePermissionMetaclass):

    def has_permission(self, request, view):
        return True

    def has_object_permission(self, request, view, obj):
        return True
```


### has_permission
has_permission is used to decide whether a request and a user are allowed to access a specific view


has_permission possesses knowledge about the request, but not about the object of the request.

As explained at the beginning, has_permission (called by check_permissions) gets executed before the view handler is executed, without explicitly calling it.


### has_object_permission
**has_object_permission is used to decide whether a specific user is allowed to interact with a specific object**

Unlike has_permission, has_object_permission isn't always executed by default:

* With an APIView, you must explicitly call check_object_permission to execute has_object_permission for all permission classes.
* With ViewSets (like ModelViewSet) or Generic Views (like RetrieveAPIView), has_object_permission is executed via check_object_permission inside a get_object method out of the box.
* has_object_permission is never executed for list views (regardless of the view you're extending from) or when the request method is POST (since the object doesn't exist yet).
* When any has_permission returns False, the has_object_permission doesn't get checked. The request is immediately rejected.


![has_permission vs has_object_permission](https://testdriven.io/static/images/blog/django/drf-permissions/permissions_execution.png)