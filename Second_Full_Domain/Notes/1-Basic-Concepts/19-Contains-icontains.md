# Contains, Icontains

In Django's ORM (Object-Relational Mapping), the `contains` and `icontains` are query methods used to perform case-sensitive and case-insensitive containment tests, respectively, on text fields. Note that the `contains` and `icontains` methods are specific to text fields in Django's ORM.

## `contains`

It is used to perform a case-sensitive containment test. It checks if a given value is contained within the field.

**Example:**

```python
from django.db import models

class MyModel(models.Model):
    text_field = models.CharField(max_length=100)

# To query for objects where the text_field contains a specific value:
MyModel.objects.filter(text_field__contains='search_value')
```

## `icontains`

It is used to perform a case-insensitive containment test. It checks if a given value is contained within the field, regardless of the case.

**Example:**

```python
from django.db import models

class MyModel(models.Model):
    text_field = models.CharField(max_length=100)

# To query for objects where the text_field contains a specific value (case-insensitive):
MyModel.objects.filter(text_field__icontains='search_value')
```

These methods can be used with other query methods to build complex queries. The double underscore notation (`__`) is used to access the fields of related models or apply specific lookup operations. In this case, it is used to specify the containment operation (`contains` or `icontains`) on the `text_field`.