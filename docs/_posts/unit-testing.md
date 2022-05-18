# Unit Testing
## Levels of testing
* Unit Testing: Testing at the function level
* Component Testing: Testing is at the library and compiled binary level
* System Testing: Tests  the external interfaces of a system which is a collection of sub-systems
* Performance Testing: Testing done at sub-system and system levels to verify timing and resource usages are acceptable

## Unit Testing
Setup -> Action -> Assert

## Test-driven Development (TDD)
* A process where the developer takes personal responsibility for the quality of their code
* Unit tests are written before the production code
Gives you immediate feedback, documents what the code is doing, drives good OOD.
Worfflow: 
RED: write a failing unit test
GREEN: write just enough production code to make that test pass
REFACTOR: Refactor the unit test and the production code to make it clean

## PyTest
### Overview
* PyTest is a python unit testing framework, which provides the ability to create Tests, Test Modules, and Test Fixtures.
* Tests are python functions with “test” at the beginning of the function name.
* Tests do verification of values using the standard python assert statement. Similar tests can be grouped together by including them in the same module or class.

### Test discovery
* PyTest will automatically discover tests when you execute.
* Classer with tests in them should have “Test” at the beginning of the class name and not have an “__init__” method.
* Filenames of test modules should start or end with “test”. (i.e. test_example.py or example_test.py).

### XUnit Style Setup and Teardown.
Unit style setup/teardown functions will execute before and after testing.
```
def setup_module():
def teardown_module():
def setup_function():
def teardown_function():
def setup_class():
def teardown_class():
def setup_method():
def teardown_method():
```

### Test Fixtures
* Test Fixtures allow for re-use of setup and teardown code across tests.
* The “pytest.fixture” decorator is applied to functions that are decorators.
```
@pytest.fixture()
def setup():
	print("Setup")
```

* Individual unit tests can specify which fixtures they want executed.
```
def test1(setup):
	assert True

@pytest.mark.usefixtures(setup)
def test2():
	assert True
```

* The “autouse” parameter can be set to True to automatically execute a fixture before each test.
```
@pytest.fixture(autouse=True)
```

#### Teardown
Test Fixtures can each have their own optional teardown code which is called after a fixture goes out of scope.
There are two methods for specifying teardown code.

1. The “yield” keyword
* When the “yield” keyword is used the code after the yield is executed after the fixture goes out of scope.
* The “yield” keyword is a replacement for the return keyword so any return values are also specified in the yield statement.
```
@pytest.fixture():
def setup:
	print("Setup!")
	yield
	print("Teardown!")
```

2. The request-context object’s “add finalizer” method
* With the add finalizer method a teardown method is defined added via the request-context’s add finalizer method.
* Multiple finalization functions can be specified.
```
@pytest.fixture():
def setup(request):
	print("Setup!")
	def teardown:
		print("Teardown!")
	request.addfinalizer(teardown)
```

#### Test Fixtures Scope
Test Fixtures can have the following four different scopes with specify how often the fixture will be called:
* Function - Run the fixture once for each test
* Class - Run the fixture one for each class of tests
* Module - Run once then the module goes in scope
* Session - The fixture is run when pytest starts

#### Test Fixture Return Objects and Parameters
* Test Fixtures can optionally return data which can be used in the test.
* The optional “params” array argument in the fixture decorator can be used to specify the data returned to the test.
* When a “params” argument is specified then the test will be called one time with each value specified.
```
@pytest.fixture(params=[1,2])
def setupData(request):
	return request.param

def test(setupData):
	print(setupData)
```

### Assert statements and exceptions
* PyTest allows the use of the built in Python assert statement for performing verifications in a unit test.
* Comparison  on all of the python data types can be performed using the standard comparison operators: <, >, <=, >= ==, and !=.
* PyTest expands on the message returned from assert failures to provide more context in the test results.

#### Compare float numbers
The pytest “approx” function can be used to verify that two floating point values are “approximately” equivalent to each other with a default tolerance of 1e-6.
```
from pytest import approx
def test_float():
	assert (0.1+0.2) == approx(0.3)
```

#### Verifying Exceptions
* In some cases we want to verify that a function throws an exception under certain conditions.
* PyTest provides the “raises” helper to perform this verification using the “with” keyword.
* If the specified exception is not raised in the code block specified after the “raises” line then the test fails.
```
from pytest import raises
def test_exceptions():
	with raises(ValueError)
		raise ValueError
```

### Command line arguments
* By default PyTest automatically discover and run all tests in all properly named models form the current working directory and sub-directories.
* Command line arguments for controlling which discovered tests actually are executed.
1. moduleName: Simply specify the module name to run only the tests in that module.
2. DirectoryName/: Runs any tests found in the specified directory.
3. -k “expression”: Matches tests found that match the evaluatable expression in the string. The string values can include module, class and function names.
4. -m “expression”:  Matches tests found that have a “pytest.mark” decorator that matches the specified expression.
* Additional arguments
1. -v: Report in verbose mode.
2. -q: Run in quiet mode.
3. -s: Don’t capture console output.
4. —ignore: Ignore the specified path when discovering tests.
5. —maxfail: Stop after the specified number of failures.
#Automation