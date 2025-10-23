# Code Examples

Quick examples showing how to use the Azure Test Track extension with different languages.

## JavaScript

```javascript
// ADO_IDs: TC_1001
test('User login with valid credentials', () => {
  // Your test code here
});

// ADO_IDs: TC_1002, TC_1003  
it('Multiple test cases in one test', () => {
  // This covers TC_1002 and TC_1003
});
```

## TypeScript

```typescript
// ADO_IDs: TC_2001
test('API endpoint returns user data', async () => {
  const response = await apiClient.get('/users');
  expect(response.status).toBe(200);
});
```

## Python

```python
# ADO_IDs: TC_3001
def test_user_login_success():
    login_page = LoginPage()
    login_page.login("user", "pass")
    assert login_page.is_logged_in()

# ADO_IDs: TC_3002, TC_3003
@pytest.mark.parametrize("username,password", [
    ("", "pass"),      # TC_3002: Empty username
    ("user", ""),      # TC_3003: Empty password  
])
def test_login_validation(username, password):
    # Test implementation
    pass
```

## Gherkin (.feature files)

```gherkin
Feature: User Login

  # ADO_IDs: TC_4001
  Scenario: Successful login
    Given user is on login page
    When user enters valid credentials
    Then user should be logged in

  # ADO_IDs: TC_4002, TC_4003
  Scenario Outline: Login validation
    When user enters "<username>" and "<password>"
    Then user should see "<message>"
    
    Examples:
      | username | password | message |
      |          | pass123  | Username required |  # TC_4002
      | user123  |          | Password required |  # TC_4003
```

## Key Rules

1. **Comment placement**: Always place `ADO_IDs` comment **above** the test
2. **Format**: Use `TC_` followed by numbers: `TC_1234, TC_5678`
3. **Multiple IDs**: Separate with commas for tests covering multiple test cases
4. **Gherkin comments**: Use `#` instead of `//`

---

For more details, see the [README](README.md).