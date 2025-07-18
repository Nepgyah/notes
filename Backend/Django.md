## General Notes
---
- Model field attributes
	- `blank` - okay to omit in forms
	- `null` - okay for the database to hold null
	- Example: When you create an object, that field needs to be filled but when you submit forms to change that object you can leave that field blank on submission
## Models
Model names should be singular and descriptive
Example
```
class Anime(models.Model):

class AnimeList(models.Model):

class GPU(models.Model):

```
### Field naming convetions
`DateTimeField`s should generally have suffix `_at`.
Example:
- `created_at`
- `updated_at`

Exceptions include dates with limits such as `available_from` or `valid_to`

`DateField`s should have suffix `date`
- `billing_date`
- `supply_date`

### Model method naming convetions
- For query methods (i.e. methods that look something up and return it), prefix with `get_`
- For setter methods (i.e. methods that set fields and call save), prefix with `set_`

### Encapsulation model mutation
Don't call a model's `save` method from anywhere but the mutator methods on the model itself

Similarly, avoid calling `ModelName.objects.create` outside the model itself. Encapsulate these in 'factory' methods. (Classmethods for the `object.create` call)

### Method 
Keep models organized by grouping them by methods with a comment
Example:
```
class SomeModel(models.Model):
    name = models.CharField(max_length=255)

    # Factories

    @classmethod
    def new(cls, name):
        return cls.objects.create(name=name)

    # Mutators

    def anonymise(self):
        self.name = ""
        self.save()

    def set_name(self, new_name):
        self.name = new_name
        self.save()

    # Queries

    def get_num_apples(self):
        return self.fruits.filter(type="APPLE").count()

    # Properties

    @property
    def is_called_dave(self):
        return self.name.lower() == "dave"
```
