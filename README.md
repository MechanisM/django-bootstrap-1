Django Bootstrap
================

Django class-based views ready to work with Twitter's Bootstrap toolkit, designed to kickstart development of webapps and sites.

Requirements
------------

* Django 1.3+
* Django 1.4+ (If you want to use SessionWizardView)

Installation
------------

Install through pip (or manually place it on your `PYTHON_PATH`).

    pip install git+http://github.com/codasus/django-bootstrap#egg=bootstrap

or just:

    pip install django-bootstrap

Configuration
-------------

Append `bootstrap` to `INSTALLED_APPS` tuple in your project's `settings.py`.

Example
-------

**urls.py**

```python
...

urlpatterns = patterns('',
    url('^', include('contact_list.urls', namespace='contact_list')),
)
```

**contact_list/models.py**

_Take a look at `test_app/contact_list/models.py`_

**contact_list/forms.py**

```python
from django import forms
from .models import Contact

class ContactForm(forms.ModelForm):
    class Meta:
        model = Contact
```

**contact_list/urls.py**

```python
from bootstrap.urls import bootstrap_patterns
from contact_list.forms import ContactForm

urlpatterns = bootstrap_patterns(ContactForm)
```

Well done! Just go to http://localhost:8000/contact

You may also create views separately using `bootstrap.urls` functions:

    bootstrap_list(r'object/', name[, view or model])
    bootstrap_create(r'object/add', name[, view or model])
    bootstrap_update(r'object/update/(?P<pk>\d+)/', name[, view or model])
    bootstrap_delete(r'object/delete/(?P<pk>\d+)/', name[, view or model])

**For example:**

```python
urlpatterns = patterns('',
        bootstrap_list(r'object/$',
                        'object_list',
                        view=ObjectListView.as_view()))
```

or

```python
urlpatterns = patterns('',
        bootstrap_list(r'object/$',
                        'object_list',
                        model=Object))
```

MIT License
-----------

Copyright (c) 2011 Caio Ariede and Codasus Technologies.

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
