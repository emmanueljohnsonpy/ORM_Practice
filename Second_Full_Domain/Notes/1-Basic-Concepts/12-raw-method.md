# Django's Raw Method

Django's Object-Relational Mapping (ORM) includes a "raw method" feature that enables direct execution of raw SQL queries through the Django ORM. It provides a way to interact with the database using custom SQL statements instead of relying solely on the ORM's query API. The raw method is available on the model's manager object (objects) and can be accessed as `Model.objects.raw(raw_query, params=None)`. Here, Model refers to the Django model on which you want to execute the raw SQL query. The raw_query parameter is a string containing the SQL query you want to execute. You can include placeholders for parameters in the query using %s or %(parameter_name)s syntax and provide the corresponding values as a list or dictionary using the params parameter.

Here's an example to illustrate the usage of the raw method:

```python
from django.db import models

class MyModel(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()

# Executing a raw SQL query
raw_query = "SELECT * FROM myapp_mymodel WHERE age > %s"
results = MyModel.objects.raw(raw_query, [25])

# Accessing the results
for obj in results:
    print(obj.name, obj.age)
```

In the example above, we execute a raw SQL query using the raw method of the MyModel.objects manager. The query selects all objects from the myapp_mymodel table where the age is greater than 25. The results variable contains the queryset representing the retrieved objects. We can iterate over the results and access the object's attributes (name and age in this case) as usual.

However, it's important to exercise caution when using raw SQL queries as they bypass some of Django's built-in protections and may introduce security risks or compatibility issues with different database backends. It's recommended to use the ORM's query API whenever possible and resort to raw queries only when necessary.