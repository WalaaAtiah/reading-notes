# Read -20 : Django Models

## Using Models: [source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models)

* **Django web applications access and manage data through Python objects referred to as models. Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms,**
  
  ![image](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models/local_library_model_uml.svg)

##  Model primer
### Model definition
**Models are usually defined in an application's models.py file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata. The code fragment below shows a "typical" model, named MyModelName:**

    from django.db import models
    from django.urls import reverse
    
    class MyModelName(models.Model):
        """A typical class defining a model, derived from the Model     class."""
    
        # Fields
        my_field_name = models.CharField(max_length=20,     help_text='Enter field documentation')
        # …
    
        # Metadata
        class Meta:
            ordering = ['-my_field_name']
    
        # Methods
        def get_absolute_url(self):
            """Returns the URL to access a particular instance of     MyModelName."""
            return reverse('model-detail-view', args=[str(self.id)])
    
        def __str__(self):
            """String for representing the MyModelName object (in     Admin site etc.)."""
            return self.my_field_name
### Fields
     my_field_name = models.CharField(max_length=20, help_text='Enter field documentation')

### Field types
**Each field in your model should be an instance of the appropriate Field class. Django uses the field class types to determine a few things:**

* The column type, which tells the database what kind of data to store (e.g. INTEGER, VARCHAR, TEXT).
  
* The default HTML widget to use when rendering a form field 
  
* The minimal validation requirements, used in Django’s admin and in automatically-generated forms.

**Django ships with dozens of built-in field types; you can find the complete list in the model field reference. You can easily write your own fields if Django’s built-in ones don’t do the trick; see How to create custom model fields.**

### Metadata
    class Meta:
       ordering = ['-my_field_name']


## Django Tutorial Part 4: Django admin site:[source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)
 
 **The Django admin application can use your models to automatically build a site area that you can use to create, view, update, and delete records. This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data. The admin application can also be useful for managing data in production, depending on the type of website.**

### Advanced configuration:
* Each model has a list of individual records, identified by the string created with the model's __str__() method, and linked to detail views/forms for editing. By default, this view has an action menu at the top that you can use to perform bulk delete operations on records.
  
* The model detail record forms for editing and adding records contain all the fields in the model, laid out vertically in their declaration order.


**Call the following command, in the same directory as manage.py, to create the superuser. You will be prompted to enter a username, email address, and strong password.**

`python3 manage.py createsuperuser`

**Once this command completes a new superuser will have been added to the database. Now restart the development server so we can test the login:**

`python3 manage.py runserver`