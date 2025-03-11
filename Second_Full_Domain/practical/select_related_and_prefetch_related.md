# Using `select_related` and `prefetch_related` in Django ORM

## ForeignKey Relationship

Assuming a ForeignKey relationship from `Product` to `Category`:

```python
products = Product.objects.select_related('category').all()
```

Now you can access category data without additional queries:

```python
for product in products:
    print(product.category.name)
```

## ManyToMany Relationship

Assuming a ManyToMany relationship from `Product` to `Tag`:

```python
# Fetching all books and their related authors
books = Book.objects.prefetch_related('authors').all()

# Iterating over each book and printing its authors' names
for book in books:
    print(f"Book: {book.title}")
    print("Authors: ", [author.name for author in book.authors.all()])
```

Now you can access tags without additional queries:


