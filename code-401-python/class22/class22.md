# Read-22 : Django CRUD and Forms

## Django Forms:[source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms)

**we'll show you how to work with HTML Forms in Django,the easiest way to write forms to create, update, and delete model instances.**

### HTML Forms:
**First, a brief overview of HTML Forms. Consider a simple HTML form, with a single text field for entering the name of some "team", and its associated label:**

    <form action="/team_name_url/" method="post">
      <label for="team_name">Enter name: </label>
      <input
        id="team_name"
        type="text"
        name="name_field"
        value="Default name for team." />
      <input type="submit" value="OK" />
    </form>

**While here we just have one text field for entering the team name**

* action: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
* method: The HTTP method used to send the data: post or get.
   * The POST method should always be used if the data is going to result in a change to the server's database, because it can be made more resistant to cross-site forgery request attacks.
   * The GET method should only be used for forms that don't change user data (for example, a search form). It is recommended for when you want to be able to bookmark or share the URL.

### Django form handling process
**he view gets a request, performs any actions required including reading data from the models, then generates and returns an HTML page (from a template, into which we pass a context containing the data to be displayed). What makes things more complicated is that the server also needs to be able to process data provided by the user, and redisplay the page if there are any errors.**

<img src="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_handling_-_standard.png" alt="drawing" style="width:700px;"/>

* Based on the diagram above, the main things that Django's form handling does are:
  1. Display the default form the first time it is requested by the user.
  2. Receive data from a submit request and bind it to the form.
  3. Clean and validate the data
  4. If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
  5. If all data is valid, perform required actions (such as save the data, send an email, return the result of a search, upload a file, and so on).
  6. Once all actions are complete, redirect the user to another page.


### There are many other types of form fields, which you will largely recognize from their similarity to the equivalent model field classes:

* BooleanField
* CharField
* ChoiceField
* TypedChoiceField
* DateField
* DateTimeField
* DecimalField
* DurationField
* EmailField
* FileField
* FilePathField
* FloatField
* ImageField
* IntegerField
* GenericIPAddressField
* MultipleChoiceField
* TypedMultipleChoiceField
* NullBooleanField
* RegexField
* SlugField
* TimeField
* URLField
* UUIDField
* ComboField
* MultiValueField
* SplitDateTimeField
* ModelMultipleChoiceField
* ModelChoiceField

### Validation
    import datetime
    
    from django import forms
    
    from django.core.exceptions import ValidationError
    from django.utils.translation import gettext_lazy as _
    
    class RenewBookForm(forms.Form):
        renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")
    
        def clean_renewal_date(self):
            data = self.cleaned_data['renewal_date']
    
            # Check if a date is not in the past.
            if data < datetime.date.today():
                raise ValidationError(_('Invalid date - renewal in past'))
    
            # Check if a date is in the allowed range (+4 weeks from today).
            if data > datetime.date.today() + datetime.timedelta(weeks=4):
                raise ValidationError(_('Invalid date - renewal more than 4 weeks ahead'))
    
            # Remember to always return the cleaned data.
            return data