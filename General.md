## Importing
### Order and Grouping
1. Standard libraries
2. Core framework Package (Django, NextJs, etc)
3. Third party (DRF, MUI, etc)
4. Local (Django models, Next components, etc)

### Modules vs Objects
Its typically better to iport modules rather than specific objects. For example, instead of:
```
from django.http import HttpResponse, HttpResponseRedirect, HttpResponseBadRequest
from django.shortcuts import render, get_object_or_404
```
Prefer this:
```
from django import http, shortcuts
```

It keeps the import area cleaning and less chance of namespace collisions. Ex: two seperate modules having an the object serializer.

### Wildcard imports
Refrain from using the wildcard import
```
from .package import *
```
- It makes it difficult to trackdown where a functionality lives
- Wildcard imports can confuse static analysis tools such as mypy
**Fundementally, its better to be explicit even if its more verbose.**
