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
- PRODUCT_BASED
- INVOICE_BASED

#### discountEntity
- ADVERTISEMENT
- MEMBERSHIP
- OTHER

#### valueType
- 1 = Percentage
- 2 = Amount

## Create Discount Criteria

- **Endpoint**: `POST /v1/discount-criteria`
- **Description**: Creates a new discount criteria with the provided details.

### Request Body

```json
{
  "discount_name": "10% off on topad & bumpup combo",
  "discount_code": "TOPAD10COMBO",
  "discount_category": "PRODUCT_BASED",
  "discount_entity": "ADVERTISEMENT",
  "entity_attributes": {},
  "value_type": 1,
  "value": 0.00,
  "minimum_eligibility_amount": 0.00,
  "maximum_eligibility_amount": 0.00,
  "valid_from": "2025-07-27 00:00:00",
  "valid_to": "2025-08-31 23:59:59",
  "purchasing_criteria": {
     "top_ad": [3],
     "bump_up": [3, 7, 15]
  },
  "benefited_product_list": {},
  "flags": {
    "apply_explicit": false
  },
  "is_notification_enabled": true,
  "is_applied_to_pay_ids": true,
  "customer_pay_ref": [220512063, 220511959, 220511991, 220511992],
  "created_by": "admin"
}
```

### Response

```json
{
    "id": 53,
    "discount_name": "10% off on topad & bumpup combo",
    "discount_code": "TOPAD10COMBO",
    "discount_category": "PRODUCT_BASED",
    "discount_entity": "ADVERTISEMENT",
    "entity_attributes": {},
    "value_type": 1,
    "value": 0.00,
    "minimum_eligibility_amount": 0.00,
    "maximum_eligibility_amount": 0.00,
    "valid_from": "2025-07-27 00:00:00",
    "valid_to": "2025-08-31 23:59:59",
    "purchasing_criteria": {
        "top_ad": [
            3
        ],
        "bump_up": [
            3,
            7,
            15
        ]
    },
    "benefited_product_list": {},
    "flags": {
        "apply_explicit": false
    },
    "is_active": true,
    "is_notification_enabled": true,
    "is_applied_to_pay_ids": true,
    "customer_pay_ref": [
        220512063,
        220511959,
        220511991,
        220511992
    ],
    "created_at": "2025-07-22 13:17:10",
    "updated_at": "2025-07-22 13:17:10",
    "created_by": "admin"
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
    "id": 53,
    "discount_name": "10% off on topad & bumpup combo",
    "discount_code": "TOPAD10COMBO",
    "discount_category": "PRODUCT_BASED",
    "discount_entity": "ADVERTISEMENT",
    "entity_attributes": {},
    "value_type": 1,
    "value": 0.00,
    "minimum_eligibility_amount": 0.00,
    "maximum_eligibility_amount": 0.00,
    "valid_from": "2025-07-27 00:00:00",
    "valid_to": "2025-08-31 23:59:59",
    "purchasing_criteria": {
        "top_ad": [
            3
        ],
        "bump_up": [
            3,
            7,
            15
        ]
    },
    "benefited_product_list": {},
    "flags": {
        "apply_explicit": false
    },
    "is_active": true,
    "is_notification_enabled": true,
    "is_applied_to_pay_ids": true,
    "customer_pay_ref": [
        220512063,
        220511959,
        220511991,
        220511992
    ],
    "created_at": "2025-07-22 13:17:10",
    "updated_at": "2025-07-22 13:17:10",
    "created_by": "admin"
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
            "id": 53,
            "discount_name": "10% off on topad & bumpup combo",
            "discount_code": "TOPAD10COMBO",
            "discount_category": "PRODUCT_BASED",
            "discount_entity": "ADVERTISEMENT",
            "entity_attributes": {},
            "value_type": 1,
            "value": 0.00,
            "minimum_eligibility_amount": 0.00,
            "maximum_eligibility_amount": 0.00,
            "valid_from": "2025-07-27 00:00:00",
            "valid_to": "2025-08-31 23:59:59",
            "purchasing_criteria": {
                "top_ad": [
                    3
                ],
                "bump_up": [
                    3,
                    7,
                    15
                ]
            },
            "benefited_product_list": {},
            "flags": {
                "apply_explicit": false
            },
            "is_active": true,
            "is_notification_enabled": true,
            "is_applied_to_pay_ids": true,
            "created_at": "2025-07-22 13:17:10",
            "updated_at": "2025-07-22 13:17:10",
            "created_by": "admin"
        },
        {
            "id": 52,
            "discount_name": "10% off on topad & bumpup combo",
            "discount_code": "TOPAD10COMBO",
            "discount_category": "PRODUCT_BASED",
            "discount_entity": "ADVERTISEMENT",
            "entity_attributes": {},
            "value_type": 1,
            "value": 0.00,
            "minimum_eligibility_amount": 0.00,
            "maximum_eligibility_amount": 0.00,
            "valid_from": "2025-07-27 00:00:00",
            "valid_to": "2025-08-31 23:59:59",
            "purchasing_criteria": {
                "top_ad": [
                    3
                ],
                "bump_up": [
                    3,
                    7,
                    15
                ]
            },
            "benefited_product_list": {},
            "flags": {
                "apply_explicit": false
            },
            "is_active": true,
            "is_notification_enabled": true,
            "is_applied_to_pay_ids": true,
            "created_at": "2025-07-22 12:13:43",
            "updated_at": "2025-07-22 12:13:43",
            "created_by": "admin"
        }
    ],
    "page": 0,
    "size": 2,
    "totalElements": 29,
    "totalPages": 15,
    "first": true,
    "last": false
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
    "id": 53,
    "discount_name": "10% off on topad & bumpup combo",
    "discount_code": "TOPAD10COMBO",
    "discount_category": "PRODUCT_BASED",
    "discount_entity": "ADVERTISEMENT",
    "entity_attributes": {},
    "value_type": 1,
    "value": 0.00,
    "minimum_eligibility_amount": 0.00,
    "maximum_eligibility_amount": 0.00,
    "valid_from": "2025-07-27 00:00:00",
    "valid_to": "2025-08-31 23:59:59",
    "purchasing_criteria": {
        "top_ad": [
            3
        ],
        "bump_up": [
            3,
            7,
            15
        ]
    },
    "benefited_product_list": {},
    "flags": {
        "apply_explicit": false
    },
    "is_active": false,
    "is_notification_enabled": true,
    "is_applied_to_pay_ids": true,
    "customer_pay_ref": [
        220512063,
        220511959,
        220511991,
        220511992
    ],
    "created_at": "2025-07-22 13:17:10",
    "updated_at": "2025-07-22 13:17:10",
    "created_by": "admin"
}
```

### Error Response

```json
{
    "Error": [
        {
            "code": "RESOURCE_NOT_FOUND",
            "message": "Discount criteria not found with id: 50"
        }
    ]
}
```
