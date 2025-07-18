## Overall
---
- Test the most common outcomes of everything you can
- Test edge cases of the complex code that could have errors
- Whenever a bug occurs, write a test case before fixing it
- Add edge case tests to less critical code whenever you have time
- Don't forget to test things such as Rest Framework serializers
	- You aren't testing the serializer itself but testing if you implemented it correctly
## Test function structure
---
A unit test has three steps:
- ARRANGE: put the world in the right state for the test
- ACT: call the unit under test (if needed, capture its output)
- ASSERT: check that the right output was returned (or the right calls to the collaborators was made)

Add a blank line in between each step to aid redability
```
class TestSomeFunction:
    def test_does_something_in_a_certain_way(self):
        input = {"a": 100}

        output = some_function(input)

        assert output == 300
```
## Structure
---
- Group tests by classes based on similar cases (i.e Class testing a user signing up, Class testing a user updating their profile)
- Focus on **your custom logic**
- For each function to modify one attribute to test an invalid field, use `payload self.valid_payload.copy()` to prevent mutating the original
- Include a `tearDown(self)` function when:
	- The view works with files
	- Connect to any external APIs or Services
	- Override any settings of the class
	- **If your the tests are doing simple database work, you can omit tearDown()**
## Naming convention
`def test_[valid | invalid]_[scenario]_variant`
Examples:
- def test_valid_signup(self):
- def test_invalid_email_already_used(self):
- def test_invalid_password_all_upper(self):
### Global / Shared Data
