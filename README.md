# Discount Criteria API Documentation

This document provides details about the Discount Criteria CRUD endpoints.

## Table of Contents
- [Create Discount Criteria](#create-discount-criteria)
- [Get Discount Criteria by ID](#get-discount-criteria-by-id)
- [Get All Discount Criteria](#get-all-discount-criteria)
- [Toggle Discount Criteria Status](#toggle-discount-criteria-status)

## Field Descriptions

### Enumerated Fields
The following fields use numeric values to represent specific options:

#### discountCategory
- 1 = Product-based
- 2 = Invoice-based
- 3 = Miscellaneous

#### discountEntity
- 1 = Advertisement
- 2 = Membership
- 3 = Other

#### valueType
- 1 = Percentage
- 2 = Amount

## Create Discount Criteria

- **Endpoint**: `POST /v1/discount-criteria`
- **Description**: Creates a new discount criteria with the provided details.

### Request Body

```json
{
  "discount_name": "asdga",
  "discount_code": "asdga",
  "discount_category": "asdga",
  "discount_entity": "asdga",
  "entity_attributes": {},
  "value_type": 1,
  "value": 20.3,
  "minimum_eligibility_amount": 32.2,
  "maximum_eligibility_amount": 123.2,
  "valid_from": "2023-06-01 00:00:00",
  "valid_to": "2023-08-31 23:59:59",
  "purchasing_criteria": {},
  "benefited_product_list": {},
  "flags": {},
  "is_notification_enabled": true,
  "is_applied_to_pay_ids": true,
  "customer_pay_ref": {},
  "created_by": "string"
}
```

### Response

```json
{
    "id": 1,
    "discount_name": "asdga",
    "discount_code": "asdga",
    "discount_category": "asdga",
    "discount_entity": "asdga",
    "entity_attributes": {},
    "value_type": 1,
    "value": 20.30,
    "minimum_eligibility_amount": 32.20,
    "maximum_eligibility_amount": 123.20,
    "valid_from": "2023-06-01 00:00:00",
    "valid_to": "2023-08-31 23:59:59",
    "purchasing_criteria": {},
    "benefited_product_list": {},
    "flags": {},
    "is_active": true,
    "is_notification_enabled": true,
    "is_applied_to_pay_ids": true,
    "customer_pay_ref": {},
    "created_at": "2025-07-07 09:28:06",
    "updated_at": "2025-07-07 09:28:06",
    "created_by": "string"
}
```

## Get Discount Criteria by ID

- **Endpoint**: `GET /v1/discount-criteria/{id}`
- **Description**: Retrieves a specific discount criteria by its ID.

### Path Parameters

- `id` - The unique identifier of the discount criteria to retrieve.

### Response

```json
{
    "id": 1,
    "discount_name": "asdga",
    "discount_code": "asdga",
    "discount_category": "asdga",
    "discount_entity": "asdga",
    "entity_attributes": {},
    "value_type": 1,
    "value": 20.30,
    "minimum_eligibility_amount": 32.20,
    "maximum_eligibility_amount": 123.20,
    "valid_from": "2023-06-01 00:00:00",
    "valid_to": "2023-08-31 23:59:59",
    "purchasing_criteria": {},
    "benefited_product_list": {},
    "flags": {},
    "is_active": true,
    "is_notification_enabled": true,
    "is_applied_to_pay_ids": true,
    "customer_pay_ref": {},
    "created_at": "2025-07-07 09:28:06",
    "updated_at": "2025-07-07 09:28:06",
    "created_by": "string"
}
```

## Get All Discount Criteria

- **Endpoint**: `GET /v1/discount-criteria`
- **Description**: Retrieves a paginated list of all discount criteria.

### Query Parameters

- `page` - The page number (zero-based indexing). Default: 0
- `size` - The number of items per page. Default: 50

### Response

```json
{
    "content": [
        {
            "id": 1,
            "discount_name": "asdga",
            "discount_code": "asdga",
            "discount_category": "asdga",
            "discount_entity": "asdga",
            "entity_attributes": {},
            "value_type": 1,
            "value": 20.30,
            "minimum_eligibility_amount": 32.20,
            "maximum_eligibility_amount": 123.20,
            "valid_from": "2023-06-01 00:00:00",
            "valid_to": "2023-08-31 23:59:59",
            "purchasing_criteria": {},
            "benefited_product_list": {},
            "flags": {},
            "is_active": true,
            "is_notification_enabled": true,
            "is_applied_to_pay_ids": true,
            "customer_pay_ref": {},
            "created_at": "2025-07-07 09:28:06",
            "updated_at": "2025-07-07 09:28:06",
            "created_by": "string"
        },
        {
            "id": 2,
            "discount_name": "asdga",
            "discount_code": "asdga",
            "discount_category": "asdga",
            "discount_entity": "asdga",
            "entity_attributes": {},
            "value_type": 1,
            "value": 20.30,
            "minimum_eligibility_amount": 32.20,
            "maximum_eligibility_amount": 123.20,
            "valid_from": "2023-06-01 00:00:00",
            "valid_to": "2023-08-31 23:59:59",
            "purchasing_criteria": {},
            "benefited_product_list": {},
            "flags": {},
            "is_active": true,
            "is_notification_enabled": true,
            "is_applied_to_pay_ids": true,
            "customer_pay_ref": {},
            "created_at": "2025-07-07 09:28:10",
            "updated_at": "2025-07-07 09:28:10",
            "created_by": "string"
        }
    ],
    "page": 0,
    "size": 50,
    "totalElements": 2,
    "totalPages": 1,
    "first": true,
    "last": true
}
```

## Toggle Discount Criteria Status

- **Endpoint**: `PUT /v1/discount-criteria/{id}/toggle-status`
- **Description**: Toggles the active status of a specific discount criteria (activates if inactive, deactivates if active).

### Path Parameters

- `id` - The unique identifier of the discount criteria to toggle.

### Response

```json
{
    "id": 4,
    "discount_name": "asdga",
    "discount_code": "asdga",
    "discount_category": "asdga",
    "discount_entity": "asdga",
    "entity_attributes": {},
    "value_type": 1,
    "value": 20.30,
    "minimum_eligibility_amount": 32.20,
    "maximum_eligibility_amount": 123.20,
    "valid_from": "2023-06-01 00:00:00",
    "valid_to": "2023-08-31 23:59:59",
    "purchasing_criteria": {},
    "benefited_product_list": {},
    "flags": {},
    "is_active": false,
    "is_notification_enabled": true,
    "is_applied_to_pay_ids": true,
    "customer_pay_ref": {},
    "created_at": "2025-07-07 09:28:13",
    "updated_at": "2025-07-07 09:28:13",
    "created_by": "string"
}
```

### ✅ Success and ❌ Error Codes with Messages

| Code | Type    | Message               | Description                                        |
| ---- | ------- | --------------------- | -------------------------------------------------- |
| 200  | Success | OK                    | The request was successful.                        |
| 201  | Success | Created               | The resource was successfully created.             |
| 400  | Error   | Bad Request           | The request is invalid or missing required fields. |
| 401  | Error   | Unauthorized          | Authentication is required or has failed.          |
| 404  | Error   | Not Found             | The requested resource could not be found.         |
| 500  | Error   | Internal Server Error | An unexpected error occurred on the server.        |

