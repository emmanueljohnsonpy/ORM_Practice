
# Signals

In Django ORM, signals are a way to allow decoupled applications to get notified when certain actions
occur in the database. The basic idea is that when certain events occur, Django sends out signals, and
any interested receivers can register to be notified when those signals are sent. Django provides a set
of built-in signals that you can use, such as pre_save, post_save, pre_delete, and post_delete, which
are emitted before and after saving or deleting an object in the database. 

To use signals in Django, you typically define signal handlers, which are functions that get executed when a signal is sent. Signal
handlers can perform additional actions or trigger other processes based on the event being signaled.
Signals provide a powerful way to decouple different parts of your Django application and allow them
to react to events happening in the database. They are particularly useful when you need to perform
additional operations based on certain model actions without tightly coupling the code.

## Example of Signal Handler in Django

```python
from django.db.models.signals import pre_save
from django.dispatch import receiver
from myapp.models import MyModel

@receiver(pre_save, sender=MyModel)
def mymodel_pre_save(sender, instance, **kwargs):
    # Perform additional actions before saving MyModel instance
    # Access the instance being saved via the 'instance' parameter
    # ...
```

In this example, the `mymodel_pre_save` function is a signal handler that will be called before saving a
`MyModel` instance. You can perform any additional actions or modifications to the instance before it
is saved to the database.

## Connecting Signal Handlers

To connect a signal handler to a signal, you use the `receiver` decorator, specifying the signal you want
to handle (pre_save in this case) and the sender (the model class on which the signal is sent).

Remember to import your signal handlers in your Django app's `apps.py` file or any other file that gets
imported when the application starts so that the signal handlers are registered.