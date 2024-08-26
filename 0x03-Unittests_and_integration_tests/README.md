### Unit Tests

**What Are Unit Tests?**
- **Definition:** Unit tests are automated tests that focus on verifying the correctness of individual components (units) of code, such as functions or methods. Each unit test isolates a single piece of code and checks its output against expected results.
- **Purpose:** The primary goal of unit testing is to ensure that each part of the program works as intended. It helps catch bugs early in the development process, leading to more reliable and maintainable code.
- **Characteristics:**
  - **Isolated:** Each unit test should run independently of others, without relying on external systems (e.g., databases, APIs).
  - **Fast:** Since they test small pieces of code, unit tests should run quickly.
  - **Specific:** They are designed to test specific scenarios, often focusing on edge cases and typical usage.

**Example:**
Imagine a simple function that adds two numbers:

```python
def add(a, b):
    return a + b
```

A unit test for this function might look like this:

```python
import unittest

class TestMathFunctions(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(2, 3), 5)
        self.assertEqual(add(-1, 1), 0)
        self.assertEqual(add(0, 0), 0)

if __name__ == '__main__':
    unittest.main()
```

### Integration Tests

**What Are Integration Tests?**
- **Definition:** Integration tests verify that different modules or services within a software system work together as expected. They test the interaction between components to ensure they function correctly when combined.
- **Purpose:** Integration tests help catch issues that arise from the interaction between different parts of the system, such as incorrect data flow, miscommunication between modules, or integration errors with external systems.
- **Characteristics:**
  - **Interconnected:** They focus on the integration points between components rather than individual units.
  - **Realistic:** Integration tests often use real databases, APIs, or other external dependencies to simulate how the system will operate in production.
  - **Broader Scope:** They cover more of the application than unit tests and may include multiple functions or classes interacting together.

**Example:**
Suppose you have a system where a user can register an account, and their data is stored in a database. An integration test might check if the registration process correctly saves user data and retrieves it later.

```python
import unittest
from myapp import create_user, get_user

class TestUserIntegration(unittest.TestCase):
    def test_user_registration(self):
        user_data = {'username': 'testuser', 'password': 'securepassword'}
        create_user(user_data)
        
        retrieved_user = get_user('testuser')
        self.assertEqual(retrieved_user.username, 'testuser')
        self.assertEqual(retrieved_user.password, 'securepassword')

if __name__ == '__main__':
    unittest.main()
```

### Interview Questions and Answers

**1. What is the difference between unit tests and integration tests?**
- **Answer:** Unit tests focus on individual components of the software in isolation, ensuring that each unit functions correctly on its own. Integration tests, on the other hand, focus on testing the interaction between different components or systems to ensure they work together as expected. Unit tests are typically faster and more granular, while integration tests are broader in scope and may involve multiple systems.

**2. Why is unit testing important?**
- **Answer:** Unit testing is important because it helps developers catch bugs early in the development process, making the code more reliable and maintainable. By testing individual units in isolation, developers can ensure that each component works correctly before integrating it with others, reducing the likelihood of complex bugs later on.

**3. Can you give an example of when you would use an integration test instead of a unit test?**
- **Answer:** You would use an integration test when you need to verify the interaction between different modules or components of your system. For example, if you are testing a user registration system, an integration test would ensure that the registration process correctly stores user data in the database and retrieves it later, rather than just testing the individual functions in isolation.

**4. How do you decide which parts of your code to unit test?**
- **Answer:** The decision on which parts of the code to unit test is typically based on the complexity and importance of the code. Critical logic, edge cases, and frequently used components are often prioritized for unit testing. Code that is prone to errors or has complex conditional logic should also be unit tested. The goal is to cover as much of the core functionality as possible while focusing on areas most likely to cause issues.

**5. What challenges might you face when writing integration tests?**
- **Answer:** Some challenges when writing integration tests include managing external dependencies (e.g., databases, APIs), handling asynchronous processes, ensuring that the test environment is correctly configured, and dealing with potential flakiness in tests due to environmental factors. Integration tests can also be slower and more complex to set up and maintain compared to unit tests.

**6. How do you mock dependencies in unit tests?**
- **Answer:** Dependencies in unit tests can be mocked using libraries like `unittest.mock` in Python. Mocking allows you to simulate the behavior of external dependencies, such as APIs or databases, without actually interacting with them. This helps to keep the unit tests isolated and focused on the specific code being tested.

**7. How do you ensure your tests are maintainable?**
- **Answer:** To ensure that tests are maintainable, it's important to write clear and concise test cases, avoid duplication by using reusable test setups (fixtures), and follow consistent naming conventions. Tests should be well-documented, and any setup or teardown code should be kept minimal. Additionally, tests should be regularly reviewed and updated as the codebase evolves.

These questions and answers should give you a solid foundation for understanding unit and integration tests, as well as preparing you for related interview questions.
