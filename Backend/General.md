## Import modules,  not objects
---
Prefer to import modules of a library instead of individual objects
Good:
```
from django import http, shortcuts
```
Bad:
```
from django.http import HttpResponse, HttpResponseRedirect
from django.shortcuts import render, get_object_or_404
```
## Favor singular nouns for class names
---
Try to use singular nouns for the names of python classes. This tends to make more code readable when dealing with collection of said instances
Example:
```
user_profiles: list[UserProfile] = get_user_profiles(account)
```

### Tips for finding a singular noun when you have a plural
- An alternative to `Options`, `Details`, `Preferences`, you can use `Profile` or `Specification`
- An easy tip is to add a noun that describes the collection, such as `set` or `batch`
	- Ex: `AnimeBatch` is better than `Animes`

## Catching exceptions
---
Refrain form using the base `except:`, always try to specify the types that should be caught
Only catch the exception type in these cases:
1. **If you are re-raising the exception.** Allows you to log exceptions (if using sentry) but allow somewhere further up the call chain to handle it. For example, a top level exception handler with rest_framework
2. **If you want to provide a better experience for the end user than the default exception**
```
class MyView(generic.FormView):
    def form_valid(self, form):
        try:
            usecase.perform_action()
        except Exception:
            # This is unanticipated so let's log to Sentry...
            logger.exception("Unable to perform action")

            # ...and show a friendly message to the end user.
            msg = (
                "Something went wrong when processing your submission. "
                "We're going to look into it."
            )
            form.add_error(None, msg)
            return self.form_invalid(form)
```
## Docstrings
---
The first sentence of a docstring should complete the sentence `This function will...` 
Functions that return booleans should start with `test`
Example: `def test_meal_tast(meal):`

### Docstring vs comments
- **Docstrings** explain what the function does and are written for people who might want to use that function but are not interested in the implementation details
- **Comments** are for people who want to understand the implementation so they can change it or extend it. Common use is to explain why something has been implemented that way