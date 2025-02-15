# Aggregate Functions

In Django's Object-Relational Mapping (ORM), aggregate functions are used to perform calculations
on sets of database records and return a single result. These functions allow you to perform operations
like counting, summing, averaging, and finding the maximum or minimum value of a field across
multiple records.Django provides several built-in aggregate functions that you can use with the ORM.
Here are some commonly used aggregate functions. Note that aggregate functions are executed on
the database side, which means they are efficient for handling large datasets and can take advantage
of database optimizations.

1. **Count**: It returns the number of records that match a specified condition.
    ```python
    from django.db.models import Count
    # Count the number of books
    Book.objects.aggregate(total=Count('id'))
    ```

2. **Sum**: It calculates the sum of values in a specific field.
    ```python
    from django.db.models import Sum
    # Calculate the total price of all books
    Book.objects.aggregate(total_price=Sum('price'))
    ```

3. **Avg**: It calculates the average value of a specific field.
    ```python
    from django.db.models import Avg
    # Calculate the average rating of all books
    Book.objects.aggregate(avg_rating=Avg('rating'))
    ```

4. **Max and Min**: They find the maximum and minimum values of a specific field, respectively.
    ```python
    from django.db.models import Max, Min
    # Find the highest and lowest prices of books
    Book.objects.aggregate(max_price=Max('price'), min_price=Min('price'))
    ```

These aggregate functions can be used in combination with filters and annotations to perform more complex calculations on subsets of data in your Django models. They are typically used with the `aggregate()` method, which returns a dictionary containing the calculated results.