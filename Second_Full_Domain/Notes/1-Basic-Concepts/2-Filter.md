# FILTER in Django ORM

In Django's ORM (Object-Relational Mapping), the "filter" method is used to query the database and retrieve a subset of objects that match certain criteria. It allows you to apply conditions on fields of a model to narrow down the results.

## Basic Syntax

The basic syntax of the filter method is as follows:

```python
Model.objects.filter(field_name=value)
```

## Multiple Filters

You can also apply multiple filters using the filter method by chaining them together. In this case, both condition1 and condition2 must be satisfied for an object to be included in the result set:

```python
Model.objects.filter(condition1).filter(condition2)
```

## Example Usage

Here's an example that demonstrates the use of the filter method:

```python
from myapp.models import MyModel

# Retrieve all objects where the 'status' field is 'active'
active_objects = MyModel.objects.filter(status='active')

# Retrieve all objects where the 'quantity' field is greater than 10
filtered_objects = MyModel.objects.filter(quantity__gt=10)
```