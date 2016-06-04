# Installing 3rd party apps
A django project is composed of **apps**.  
It is easy to install and add an app to your project.

## General instructions
* Most apps are listed here: <https://www.djangopackages.com/> . Go hunt.
Look for stars.
* Once you find an interesting app, be sure to start going through
its documentation and read the requirements (python and django versions, other
requirements) and installation instructions.
* Prefer using **pip** to install the app (over downloading or cloning the 
sources)
* Follow other installation instructions from the documentation :-)
 
## Example: Installing django-extensions.
[*django-extensions*](http://django-extensions.readthedocs.io/en/latest/)
is a reusable django app.

Following the installation instructions, to use it we should:

* Run:

        pip install django-extensions
    
* Open `myproject/settings.py`, find `INSTALLED_APPS` in it , and
add the following line to the tuple:

        INSTALLED_APPS = (
            ...
            
            'django_extensions',
        )

When running `manage.py` you can now see many more commands supplied by 
*django-extensions*.
