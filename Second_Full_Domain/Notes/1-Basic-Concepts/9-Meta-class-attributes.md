
# Meta Class Attributes 

In Django's Object-Relational Mapping (ORM), a meta class is a class that provides metadata about
another class. It allows you to define various options and behaviours for a model class. One of the
options you can define in the meta class is the model's attributes.

Meta class attributes in Django ORM are defined within the nested `Meta` class inside a model class.
These attributes provide additional information about the model, such as the database table name,
ordering options, unique constraints, and more.

### Example:

```python
from django.db import models

class MyModel(models.Model):
    # Fields and methods for your model go here
    
    class Meta:
        verbose_name_plural = "My Models"
        ordering = ['created_at']
```

In the above example, the `Meta` class is defined within the `MyModel` class. It specifies two meta class
attributes:

1. `verbose_name_plural`: This attribute sets the human-readable name for the model in its plural form.
   In this case, it's set to "My Models" to be displayed in the Django admin interface.

2. `ordering`: This attribute specifies the default ordering for query sets of this model. In this case, it orders
   the query sets by the `created_at` field.

### Other Meta Class Attributes:
These meta class attributes provide additional control and customization options for your Django models. You can define various other meta class attributes, such as:
- `verbose_name`
- `db_table`
- `unique_together`
- `indexes`


These options depend on your requirements.