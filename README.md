# django-populate-admin-login-to-whole-website
How to populate the django admin login page to the whole website.
# Introduction
Instead of having two login pages for your website one for super users to access the django adminstration pages and another to access the ordinary website pages  , sometimes you only have one adminstration website and your website is already needs a super user to login also, so on this page we will preview steps how to populate the admin login system to the whole wesite.

# Steps 
1. In your applications for every view in your website you need to add @login_required decoration , so in your_app/view.py import login_required and follow the example.
```python
from django.contrib.auth.decorators import login_required
@login_required
def index(request): #< --- as an example
    # ... your code 
    
@login_required
def your_other_view_function(request):
    # ...
```

2. In your website folder create views.py and add the following to redirect the login page to the admin login one.

```python
from django.shortcuts import redirect

def login(request):
    return redirect ('admin:login')
```

3. In website urls.py import the created views.py in the previews step and add the regular expression r'^account/login' pattern to the url pattern list as follow.

```python
from django.urls import re_path
from .views import login
urlpatterns = [
    # .... your patterns
    re_path(r'^accounts/login/',login)
]
```
# Django Version 
  Django verion used in this preview was 2.1.


