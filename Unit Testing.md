## Overall
- Test the most common outcomes of everything you can
- Test edge cases of the complex code that could have errors
- Whenever a bug occurs, write a test case before fixing it
- Add edge case tests to less critical code whenever you have time
- Don't forget to test things such as Rest Framework serializers
	- You aren't testing the serializer itself but testing if you implemented it correctly
## Naming convention
The name of a test should consist of three parts
1. Name of the method being tested
2. Scenarios under which the method is being tests
3. Expected behavior when the scenario is invoked
```
EditAnime_Valid_UpdatesAnime
EditAnime_InvalidName_BadRequest
EditAnime_InvalidEpisodeCount_BadRequest
EditAnime_InvalidAnimeIDArg_NotFound
```
## Test function structure
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
## Test grouping
A reasonable way to organize the whole unit tests in a file
- Test unauthenticated urls (if applicable)
- Test for not found in urls with arguments
- Continue with each group of tests of an endpoint

Common tests for a single endpoint
- Test for the expected result
- Test a single error per test
Common cases to test for in a endpoint
- Invalid payload arguments (out of bounds, data type, etc)
- Missing payload
