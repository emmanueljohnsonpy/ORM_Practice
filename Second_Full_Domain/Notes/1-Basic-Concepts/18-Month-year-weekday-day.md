# Month, Year, Weekday, Day

In Django ORM, you can use the `Extract` function to retrieve specific components of a date or datetime field. To get the month, year, weekday, and day from a date field, you can use the following methods:

1. **Month**: Use the `ExtractMonth` function to extract the month from a date field.
    ```python
    from django.db.models.functions import ExtractMonth
    result = MyModel.objects.annotate(month=ExtractMonth('date_field'))
    ```
    This will annotate the `month` field with the month extracted from the `date_field` in the `MyModel` queryset.

2. **Year**: Similar to the month, you can use the `ExtractYear` function to extract the year from a date field.
    ```python
    from django.db.models.functions import ExtractYear
    result = MyModel.objects.annotate(year=ExtractYear('date_field'))
    ```
    This will annotate the `year` field with the year extracted from the `date_field`.

3. **Weekday**: The weekday can be obtained using the `ExtractWeekDay` function. Note that the weekday is represented as an integer, where Monday is 1 and Sunday is 7.
    ```python
    from django.db.models.functions import ExtractWeekDay
    result = MyModel.objects.annotate(weekday=ExtractWeekDay('date_field'))
    ```
    This will annotate the `weekday` field with the weekday extracted from the `date_field`.

4. **Day**: To extract the day from a date field, you can use the `ExtractDay` function.
    ```python
    from django.db.models.functions import ExtractDay
    result = MyModel.objects.annotate(day=ExtractDay('date_field'))
    ```
    This will annotate the `day` field with the day extracted from the `date_field`.

Make sure to replace `'date_field'` with the actual field name in your model. The result queryset will contain the annotated fields (`month`, `year`, `weekday`, `day`) with the respective values extracted from the date field.