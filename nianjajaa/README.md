# Golang Unit Testing

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   26-02-2025             | v1          | Aayush Verma   |26-02-2025    |  Internal Reviewer | Komal Jaiswal |

## Table of Contents

- [Introduction](#introduction)
- [What is Unit Testing?](#what-is-unit-testing)
- [Why Unit Testing?](#why-unit-testing)
- [General Workflow](#General-Workflow)
- [Different Tools for Unit Testing](#different-tools-for-unit-testing)
- [Comparison of Different Tools](#comparison-of-different-tools)
- [Advantages of Unit Testing](#advantages-of-unit-testing)
- [Proof of Concept](#proof-of-concept-poc)
- [Best Practices of Unit Testing](#best-practices-of-unit-testing)
- [Recommendations / Conclusion](#Recommendations-/-Conclusion)
- [Contact](#Contact)
- [References](#References)




## Introduction
Unit testing is a crucial aspect of software development that ensures individual components of an application function as expected. In Golang, unit testing is built into the standard library, making it easy to implement and maintain.

---

## What is Unit Testing?
Unit testing is a software testing technique where individual functions or components of an application are tested independently to verify correctness. These tests help catch bugs early, improve code quality, and enhance maintainability.

---

## Why Unit Testing?
- **Built-in Testing Package**: Golang provides a native `testing` package for writing and executing unit tests.
- **Performance and Simplicity**: Golang’s testing framework is lightweight and easy to use.
- **Automated Testing**: Supports automated test execution using `go test`.
- **Benchmarking and Example Tests**: Built-in support for performance testing and documentation through examples.

---

## General Workflow



**Description of Flow Diagram**

| **Steps** | **Description** |
| ------------- | --------------- |
| **Directory** | Create a new directory named `Golang-testing` |
| **Clone Git Repository** | Clone the Git repository `employee-API.git` into the current directory |
| **Install Go** | Install Go programming language using the Snap package manager |
| **Run Unit Tests** | Execute unit tests for the current codebase |
| **Run All Tests** | Run tests recursively for all packages |
| **Run Tests with Verbose and Coverage** | Execute tests with verbose output and coverage information |
| **Generate Coverage Profile** | Create a coverage profile file `coverage.out` for further analysis |
| **Generate HTML Report** | Convert the coverage profile to an HTML report for detailed visualization |
| **Completion** | The flow is completed, and the necessary steps for testing and coverage analysis have been executed |

---

## Different Tools for Unit Testing

| **Tool**            | **Description** | **Key Features** | **Use Cases** |
|---------------------|-----------------------------------------------------|-----------------------------------------|----------------------------------------|
| Testing          | The default Go testing package, built into the standard library. | - Simple and lightweight<br>- Uses `Test*` functions<br>- Supports benchmarks and examples | Basic unit tests, benchmarking, and example-based documentation. |
| **Testify**        | A powerful testing framework that enhances Go’s standard `testing` package. | - Better assertions (e.g., `assert.Equal`, `require.NotNil`)<br>- Mocking support via `mock` package | Writing expressive unit tests with better readability and mocking capabilities. |
| **Ginkgo & Gomega** | A Behavior-Driven Development (BDD) testing framework for Go. | - Structured in a BDD format (`Describe`, `It`, `BeforeEach`)<br>- Uses Gomega matchers (`Expect`, `HaveOccurred`) | Writing tests in a more structured, BDD style, useful for complex applications. |
| **GoMock**         | A mocking framework for Go, used alongside `testing`. | - Generates mocks using `mockgen`<br>- Works well with interfaces | Mocking dependencies for testing services, repositories, etc. |
| **Goconvey**       | A testing framework with a web-based UI and live results. | - Auto-refresh UI for real-time feedback<br>- BDD-style syntax | Writing tests with real-time feedback and an interactive UI. |
| **httptest**       | A package in the standard library for testing HTTP servers and handlers. | - Provides `httptest.NewRecorder()` for response capture<br>- Simulates HTTP requests easily | Testing HTTP handlers, APIs, and server behavior. |

---

## Comparison of Different Tools
| Tool         | Features                           | Pros                                      | Cons                                     |
|-------------|----------------------------------|-------------------------------------------|------------------------------------------|
| `testing`   | Built-in, simple, lightweight   | No external dependencies                 | Basic assertions only                    |
| Testify     | Rich assertions, mocking       | Readable and concise tests               | Requires external library                |
| Ginkgo      | BDD-style, structured tests    | Improves readability                     | More complex setup                       |
| GoMock      | Mocking support for interfaces | Helps with unit testing in isolation     | Requires additional configuration        |
| Goconvey    | Live UI, automatic testing     | Real-time feedback                       | UI setup required                        |
| httptest    | HTTP server testing            | Ideal for API testing                    | Specific to HTTP handlers                |

---

## Advantages of Unit Testing 


| **Benefit**                     | **Description** |
|----------------------------------|--------------------------------------------------|
| **Early Bug Detection**          | Identifies defects early in the development cycle, reducing costs and effort. |
| **Improved Code Quality**        | Enforces better coding practices and maintains high code standards. |
| **Facilitates Refactoring**      | Allows safe and reliable code changes without breaking functionality. |
| **Faster Debugging**             | Helps isolate and fix issues quickly, improving development efficiency. |
| **Continuous Integration Support** | Works seamlessly with CI/CD pipelines, ensuring automated testing and deployment. |


---

## Proof of Concept (POC)

[link](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-84/Application%20CI%20Design/GoLang%20CI%20Checks/Unit%20Testing/POC/README.md)

---

## Best Practices of Unit Testing

| **Best Practice**                     | **Description** |
|----------------------------------------|-------------------------------------------------------------|
| **Keep Tests Independent**             | Avoid dependencies between tests to ensure reliability. |
| **Use Table-Driven Tests**             | Improve maintainability by structuring tests with multiple cases. |
| **Mock External Dependencies**         | Use mocking frameworks like `GoMock` to isolate unit tests. |
| **Use Assertions for Readability**     | Utilize `Testify` for clearer and more readable assertions. |
| **Run Tests Automatically**            | Integrate tests into CI/CD pipelines for continuous validation. |
| **Measure Code Coverage**              | Use `go test -cover` to track how much code is tested. |
| **Use Benchmarks for Performance Testing** | Implement `Benchmark` functions to measure execution speed. |

---

## Recommendation and Conclusion
Unit testing in Golang is efficient and straightforward due to its built-in testing support. Choosing the right framework depends on project complexity and requirements. For general testing, the `testing` package suffices, while for advanced needs, `Testify` and `Ginkgo` offer enhanced features. 

---

## Contact Information

| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## References
- [Golang Official Testing Documentation](https://golang.org/pkg/testing/)
- [Testify GitHub Repository](https://github.com/stretchr/testify)
- [Ginkgo BDD Testing Framework](https://onsi.github.io/ginkgo/)
