
# Select Related and Prefetch Related 

In Django's ORM (Object-Relational Mapping), "prefetch_related" and "select_related" are methods
that allow you to optimize database queries by reducing the number of database hits when dealing
with related objects. By using select_related and prefetch_related, you can optimize your Django
queries and reduce the number of database hits, improving the performance of your application.

## 1. select_related

The `select_related` method is used to retrieve related objects using a SQL join. It works for ForeignKey and OneToOneField relationships. When you use `select_related`, Django performs a SQL join to fetch the related object(s) in the same database query, reducing the number of database hits.

### Example:

```python
from django.contrib.auth.models import User
from myapp.models import UserProfile

# Fetches the User and its related UserProfile using a single database query
user = User.objects.select_related('profile').get(username='john')

# Access the related UserProfile without extra database queries
print(user.profile.bio)
```

In this example, `select_related` is used to fetch the `UserProfile` related to a `User` in a single database query.

## 2. prefetch_related

The `prefetch_related` method is used for fetching related objects efficiently in a separate query. It works for ManyToManyField and reverse ForeignKey relationships. When you use `prefetch_related`, Django fetches the related objects in a separate query but caches them, allowing efficient access without additional database hits.

### Example:

```python
from myapp.models import Category, Product

# Fetches all categories and prefetches related products
categories = Category.objects.prefetch_related('products').all()

# Access the related products without extra database queries
for category in categories:
    for product in category.products.all():
        print(product.name)
```

In this example, `prefetch_related` is used to fetch all categories and prefetch the related products. This avoids additional database queries when accessing the products for each category.