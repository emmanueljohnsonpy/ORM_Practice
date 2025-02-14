# Managers in Django ORM

In Django ORM (Object-Relational Mapping), the term "managers" refers to a feature that allows you to query the database using model classes. Managers are responsible for retrieving data from the database and performing various operations like filtering, ordering, and aggregating the data.

By default, Django provides a manager called `objects` for every model class. This manager is used to perform common database operations such as creating, retrieving, updating, and deleting objects. For example, you can use the `objects` manager to retrieve all instances of a model or filter the instances based on certain criteria. By utilizing managers, you can centralize and organize your database queries within your model classes, promoting code reuse and maintaining a clean and expressive codebase.

## Example of Using the `objects` Manager

```python
from django.db import models

class MyModel(models.Model):
    # Fields definition
    pass

# Retrieve all instances of MyModel
instances = MyModel.objects.all()
```

## Custom Managers in Django

In addition to the default manager, you can define custom managers in Django. Custom managers allow you to encapsulate complex query logic or create reusable query sets tailored to your specific needs. To define a custom manager, you need to create a class that inherits from `django.db.models.Manager` or its subclasses.

### Example of Defining a Custom Manager

```python
from django.db import models

class CustomManager(models.Manager):
    def get_custom_queryset(self):
        # Custom query logic
        return self.get_queryset().filter(...)  # Add filtering logic here

class MyModel(models.Model):
    # Fields definition
    pass
    
    # Custom manager
    custom_manager = CustomManager()

# Use the custom manager to retrieve instances
custom_instances = MyModel.custom_manager.get_custom_queryset()
```

In this example, we created a custom manager called `CustomManager` that provides a method `get_custom_queryset()` to retrieve a custom queryset based on specific criteria. We then defined the `custom_manager` attribute in the `MyModel` class, which allows us to access the custom manager and perform queries using the defined method.

