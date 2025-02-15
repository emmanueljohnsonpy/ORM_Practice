# `exclude()`

In Django's ORM (Object-Relational Mapping), the `exclude()` method is used to construct a query that excludes certain objects from the result set based on specific conditions. The `exclude()` method is typically used in conjunction with the `filter()` method to narrow down the queryset. While the `filter()` method allows you to specify conditions that the objects must meet to be included in the queryset, the `exclude()` method allows you to specify conditions that the objects must not meet to be included in the queryset.

## Example

Here's an example to illustrate the usage of `exclude()`:

```python
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.CharField(max_length=100)
    published = models.BooleanField(default=False)

# Retrieve all books that are not published
not_published_books = Book.objects.exclude(published=True)

# Retrieve all books that are not written by a specific author
not_author_books = Book.objects.exclude(author="John Doe")
```

In the first example, the `exclude()` method is used to retrieve all books that are not published. In the second example, it's used to retrieve all books that are not written by a specific author. You can chain multiple `exclude()` calls together to create more complex querysets. Django's ORM provides various lookup options and operators that can be used within `exclude()` to define the conditions.