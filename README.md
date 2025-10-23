<p align="center">
  <img src="https://github.com/TheCollegeHub/azure-test-track-vscode-extension/blob/main/extension-logo.png" width="400" style="height: auto; display: block; margin: 0 auto;">
</p>

# Azure Test Track - Extension (VS CODE)

It is an extension designed to simplify the integration between your automated tests and Azure DevOps. It allows you to easily associate your tests with Azure DevOps test cases, automatically populating the Associated Automation tab with all relevant information and updating the automation status to Automated. This tool aims to enhance traceability and efficiency in the testing process, ensuring quick and accurate linking between code and tests in Azure DevOps.

To know more about the full package of `azure-test-track` and know more things you can do, please, check this link: [azure-test-track](https://github.com/TheCollegeHub/azure-test-track)

## Features

The azure-test-track extension provides functionalities for associating automated tests with Azure DevOps test cases. It offers two different commands for associating tests with Azure DevOps:

- Associate Test Case (Auto): Automatically associates the test case based on the test name extracted from the code.
- Associate Test Case (Custom): Manually associate the test case by entering the test name and ID.

### Features:
- Automatically associates test cases with the related automation code.
- Supports associating test cases based on pre-defined automation test names.
- Allows users to manually associate tests by specifying the test case ID and name.
- Supports multiple test types: Unit, Component, API, and E2E.
- Provides a convenient way to integrate with Azure DevOps and track test cases.
- Automatically associates all automated tests with the Azure Test Cases for all file via comments.
- The extension provides clear visual indicators that show which Azure Test Cases are actually associated with the automated tests.
- **NEW:** Full support for Gherkin syntax (.feature files) - associate BDD scenarios with Azure DevOps test cases.

    Tip: You can use this extension to streamline your testing process in Azure DevOps, improving the traceability and automation of test management.

## 📋 Code Examples

For comprehensive examples of how to use this extension with different programming languages and testing frameworks, see our **[Code Examples Guide](EXAMPLE_CODE.md)**.

The examples include:
- **JavaScript/TypeScript**: Jest, testing-library, API testing
- **Python**: pytest, Selenium WebDriver, parametrized tests  
- **Gherkin**: Feature files, scenarios, scenario outlines
- **Best Practices**: Comment placement, naming conventions, multiple test case association

## Requirements

This extension has the following requirements:

VS Code version: 1.95 or later.
Azure DevOps Setup: Ensure you have the following environment variables set up for Azure DevOps:
- ADO_ORGANIZATION
- ADO_PROJECT
- ADO_PERSONAL_ACCESS_TOKEN
- ADO_COMPANY_EMAIL

## How to Use
To associate a test case manually, follow these steps:

### Option 1
1. **Select the test line:** Click on the line where your test case is defined, which should start with:
   - `test(` or `it(` (JavaScript/TypeScript)
   - `def test_` (Python)  
   - `Scenario:` or `Scenario Outline:` (Gherkin/.feature files)

2. **Right-click and select the command:** Right-click the selected line and choose the `Associate Test to Azure DevOps using Test Name` option from the context menu to manually associate the test filling the Test Case ID and Test Case Type.

### Option 2
1. **Use the command palette:** Alternatively, press Ctrl+Shift+P (Windows/Linux) or Cmd+Shift+P (macOS), type `Associate Test to Azure DevOps filling Test Name`, and select the command to manually enter all necessary information for the association.

2. **Fill in the details:** A series of prompts will appear asking you to:

    - Enter the Test Case ID in Azure DevOps.
    - Provide the Test Case Name.
    - Choose the type of test (Unit, Component, or E2E).

After filling in all the details, the extension will associate the test case with the specified automation code.

### Option 3
1. **Insert the comments**: In the test file, add the ***comments*** with the test IDs above the test function:

   **JavaScript/TypeScript/Python:**
   ```javascript
   // ADO_IDs: TC_1234, TC_5678
   test('Your test name', () => { ... });
   ```

   **Gherkin (.feature files):**
   ```gherkin
   # ADO_IDs: TC_1234, TC_5678
   Scenario: User can login successfully
   ```

2. **Use the command palette:** Alternatively, press Ctrl+Shift+P (Windows/Linux) or Cmd+Shift+P (macOS), type `Associate IDs from Comments`, and select the ***Test Type*** for the associations.

After the command is executed, it will scan for all `ADO_IDs` and associates all ids with the automated test in `Azure Test Case`

**Note:** In your Azure Devops Test Case, the `Associated Automation` tab will be filled with all this informations and the `Automation Status` will be changed by `Automated`.

## Visualization Option
1. In the test file, run the `View/Hide All Associated Automated Tests` command.
2. Look at your code. Lines of code associated with test cases will have a green indicator `✓ Associated`, and unassociated lines will have a red indicator `✗ Unassociated`.

## Supported Languages

The extension supports the following languages and patterns:

- **JavaScript/TypeScript**: `test()`, `it()` functions
- **Python**: `def test_` functions  
- **Gherkin (.feature files)**: `Scenario:`, `Scenario Outline:` statements

## Known Issues

- There may be issues with environment variable configurations not being recognized when VS Code is run in certain environments.

## Release Notes

For more details, See the [ChangeLog](CHANGELOG.md).

-----
**Enjoy!**
