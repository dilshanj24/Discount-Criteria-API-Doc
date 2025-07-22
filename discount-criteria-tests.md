# Discount Criteria Unit Tests Documentation

## Overview

This document provides a comprehensive overview of the unit tests implemented for the Discount Criteria module in the Discount Manager application. The Discount Criteria module is responsible for managing discount rules and conditions that determine when and how discounts are applied to purchases.

The unit tests cover both the service layer (business logic) and the controller layer (REST API endpoints) to ensure that all CRUD (Create, Read, Update, Delete) operations function correctly and handle edge cases appropriately.

## Technologies & Tools Used

The following technologies and tools were used to implement and run the unit tests:

| Technology | Description |
|------------|-------------|
| **JUnit 4** | Testing framework for Java applications |
| **Mockito** | Mocking framework for unit tests |
| **Spring Boot Test** | Testing utilities for Spring Boot applications |
| **MockMvc** | For testing Spring MVC controllers without starting a full HTTP server |
| **Jackson** | For JSON serialization/deserialization in tests |
| **AssertJ/Hamcrest** | For fluent assertions in tests |

## Test Cases Covered

### Service Layer Tests

| Operation | Test Method | Purpose | Expected Behavior | Mocking |
|-----------|-------------|---------|------------------|---------|
| **Create** | `testCreateDiscountCriteria_Success` | Verifies that a discount criteria can be successfully created | The service should save the entity and return a response model with the correct values | Repository's save method is mocked to return a predefined entity |
| **Read** | `testGetDiscountCriteriaById_Success` | Verifies that a discount criteria can be retrieved by its ID | The service should return the correct discount criteria for a given ID | Repository's findById method is mocked to return an Optional containing the entity |
| **Read** | `testGetDiscountCriteriaById_NotFound` | Verifies that an appropriate exception is thrown when a discount criteria is not found | The service should throw a ResourceNotFoundException | Repository's findById method is mocked to return an empty Optional |
| **Read** | `testGetAllDiscountCriteria_Success` | Verifies that all discount criteria can be retrieved with pagination | The service should return a paged response with the correct content and pagination metadata | Repository's findAll method is mocked to return a Page object with test entities |
| **Update** | `testToggleDiscountCriteriaStatus_Success` | Verifies that a discount criteria's active status can be toggled | The service should toggle the isActive flag and return the updated entity | Repository's findById and save methods are mocked |
| **Update** | `testToggleDiscountCriteriaStatus_NotFound` | Verifies that an appropriate exception is thrown when trying to toggle a non-existent discount criteria | The service should throw a ResourceNotFoundException | Repository's findById method is mocked to return an empty Optional |
| **Special Case** | `testCustomerPayRefTransformation` | Verifies that the customer pay reference JSON is correctly transformed | The service should transform an array of customer pay references into an object with initial_list and applicable_list | Repository's save method is mocked to capture and return the transformed entity |

### Controller Layer Tests

| Operation | Test Method | Purpose | Expected Behavior | Mocking |
|-----------|-------------|---------|------------------|---------|
| **Create** | `testCreateDiscountCriteria_Success` | Verifies that the API endpoint correctly handles valid discount criteria creation requests | The endpoint should return a 201 Created status and the created entity | Service's createDiscountCriteria method is mocked to return a response model |
| **Create** | `testCreateDiscountCriteria_BadRequest` | Verifies that the API endpoint correctly handles invalid discount criteria creation requests | The endpoint should return a 400 Bad Request status | No mocking needed as validation happens before the service is called |
| **Read** | `testGetDiscountCriteriaById_Success` | Verifies that the API endpoint correctly retrieves a discount criteria by ID | The endpoint should return a 200 OK status and the requested entity | Service's getDiscountCriteriaById method is mocked to return a response model |
| **Read** | `testGetDiscountCriteriaById_NotFound` | Verifies that the API endpoint correctly handles requests for non-existent discount criteria | The endpoint should return a 404 Not Found status | Service's getDiscountCriteriaById method is mocked to throw a ResourceNotFoundException |
| **Read** | `testGetAllDiscountCriteria_Success` | Verifies that the API endpoint correctly retrieves all discount criteria with pagination | The endpoint should return a 200 OK status and a paged response | Service's getAllDiscountCriteria method is mocked to return a paged response model |
| **Update** | `testToggleDiscountCriteriaStatus_Success` | Verifies that the API endpoint correctly toggles a discount criteria's status | The endpoint should return a 200 OK status and the updated entity | Service's toggleDiscountCriteriaStatus method is mocked to return a response model with isActive set to false |
| **Update** | `testToggleDiscountCriteriaStatus_NotFound` | Verifies that the API endpoint correctly handles toggle requests for non-existent discount criteria | The endpoint should return a 404 Not Found status | Service's toggleDiscountCriteriaStatus method is mocked to throw a ResourceNotFoundException |

## Test Results Summary

All tests for the Discount Criteria module have been executed successfully, demonstrating that:

1. The service layer correctly implements all CRUD operations for discount criteria
2. The controller layer correctly exposes and handles API endpoints for these operations
3. Error cases are properly handled with appropriate HTTP status codes and exceptions
4. Edge cases, such as the transformation of customer pay references, are correctly implemented

The tests cover both positive scenarios (successful operations) and negative scenarios (error handling), ensuring robust functionality of the Discount Criteria module.

Notable findings:
- The customer pay reference transformation logic correctly converts an array of references into a structured object with initial_list and applicable_list
- The toggle status functionality correctly flips the isActive flag of a discount criteria
- Proper validation is in place to reject invalid discount criteria creation requests
- Appropriate error handling is implemented for not found scenarios

These tests provide confidence that the Discount Criteria module functions as expected and handles various scenarios correctly.