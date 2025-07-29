# Discount Criteria Create Endpoint Data Contract

This document describes the data contract for creating discount criteria in the Discount Manager API.

## Endpoint Details

- **URL**: `/v1/discount-criteria`
- **Method**: POST
- **Content-Type**: application/json
- **Produces**: application/json

## Request Body

The request body should be a JSON object with the following fields:

| Field | Type | Required | Description | Validation Rules |
|-------|------|----------|-------------|-----------------|
| `discount_name` | String | Yes | Name of the discount criteria | Must not be blank. Must be unique. |
| `discount_code` | String | No | Code for the discount criteria | Must be unique if provided. |
| `discount_category` | String | Yes | Category of the discount | Must not be null. If "PRODUCT_BASED", purchasing_criteria is required. |
| `discount_entity` | String | Yes | Entity the discount applies to | Must not be null. |
| `entity_attributes` | JSON Object | No | Attributes of the entity | Must be a valid JSON object. |
| `value_type` | Integer | Yes | Type of value (0 for fixed amount, 1 for percentage) | Must not be null. |
| `value` | Decimal | Yes | Value of the discount | Must be positive. If value_type is 1 (percentage), cannot exceed 100. |
| `minimum_eligibility_amount` | Decimal | No | Minimum amount to be eligible for the discount | Must be positive or zero if provided. |
| `maximum_eligibility_amount` | Decimal | No | Maximum amount to be eligible for the discount | Must be positive or zero if provided. |
| `valid_from` | String | No | Start date and time of the discount validity | Format: "yyyy-MM-dd HH:mm:ss" |
| `valid_to` | String | No | End date and time of the discount validity | Format: "yyyy-MM-dd HH:mm:ss" |
| `purchasing_criteria` | JSON Object | Conditional | Criteria for purchasing | Required if discount_category is "PRODUCT_BASED". Must not be an empty object in that case. |
| `benefited_product_list` | JSON Object | No | List of products that benefit from the discount | Must be a valid JSON object if provided. |
| `flags` | JSON Object | No | Flags for the discount | Must be a valid JSON object if provided. |
| `available_platforms` | JSON Object | No | Platforms where the discount is available | Must be a valid JSON object if provided. |
| `is_notification_enabled` | Boolean | No | Whether notifications are enabled for this discount | - |
| `customer_pay_ref` | JSON Array | No | Customer pay references | Must be a valid JSON array if provided. |
| `created_by` | String | Yes | User who created the discount | Must not be blank. |

## Response

### Success Response

- **Status Code**: 201 (Created)
- **Content**: JSON object with the following fields:

| Field | Type | Description |
|-------|------|-------------|
| `id` | Long | Unique identifier for the created discount criteria |
| `discount_name` | String | Name of the discount criteria |
| `discount_code` | String | Code for the discount criteria |
| `discount_category` | String | Category of the discount |
| `discount_entity` | String | Entity the discount applies to |
| `entity_attributes` | JSON Object | Attributes of the entity |
| `value_type` | Integer | Type of value (0 for fixed amount, 1 for percentage) |
| `value` | Decimal | Value of the discount |
| `minimum_eligibility_amount` | Decimal | Minimum amount to be eligible for the discount |
| `maximum_eligibility_amount` | Decimal | Maximum amount to be eligible for the discount |
| `valid_from` | String | Start date and time of the discount validity |
| `valid_to` | String | End date and time of the discount validity |
| `purchasing_criteria` | JSON Object | Criteria for purchasing |
| `benefited_product_list` | JSON Object | List of products that benefit from the discount |
| `flags` | JSON Object | Flags for the discount |
| `available_platforms` | JSON Object | Platforms where the discount is available |
| `is_active` | Boolean | Whether the discount is active |
| `is_notification_enabled` | Boolean | Whether notifications are enabled for this discount |
| `customer_pay_ref` | JSON Object | Customer pay references (transformed from the input array) |
| `created_at` | String | Date and time when the discount criteria was created |
| `updated_at` | String | Date and time when the discount criteria was last updated |
| `created_by` | String | User who created the discount |

### Error Responses

- **Status Code**: 400 (Bad Request)
  - When validation fails for the request body
  - When a discount criteria with the same name already exists
  - When a discount criteria with the same code already exists
  - When value_type is 1 (percentage) and value exceeds 100
  - When discount_category is "PRODUCT_BASED" and purchasing_criteria is missing or empty
  - When customer_pay_ref is provided but is not a valid JSON array

- **Status Code**: 500 (Internal Server Error)
  - When an unexpected error occurs during processing

## Example

### Request

```json
{
  "discount_name": "10% off on bumpup combo",
  "discount_code": "TOPAD10COssMBO",
  "discount_category": "PRODUCT_BASED",
  "discount_entity": "ADVERTISEMENT",
  "entity_attributes": null,
  "value_type": 2,
  "value": 1,
  "minimum_eligibility_amount": 0.00,
  "maximum_eligibility_amount": 0.00,
  "valid_from": "2025-07-27 00:00:00",
  "valid_to": "2025-08-31 23:59:59",
  "purchasing_criteria": {"top_ad": [3, 7, 15], "bump_up": [7]},
  "benefited_product_list": {},
  "flags": null,
  "available_platforms": ["WEB", "MOBILE", "POS"],
  "is_notification_enabled": true,
  "customer_pay_ref": [220512063, 220511959, 220511991, 220511992],
  "created_by": "admin"
}
```

### Response

```json
{
    "id": 142,
    "discount_name": "10% off on bumpup combo",
    "discount_code": "TOPAD10COssMBO",
    "discount_category": "PRODUCT_BASED",
    "discount_entity": "ADVERTISEMENT",
    "entity_attributes": null,
    "value_type": 2,
    "value": 1,
    "minimum_eligibility_amount": 0.00,
    "maximum_eligibility_amount": 0.00,
    "valid_from": "2025-07-27 00:00:00",
    "valid_to": "2025-08-31 23:59:59",
    "purchasing_criteria": {
        "top_ad": [
            3,
            7,
            15
        ],
        "bump_up": [
            7
        ]
    },
    "benefited_product_list": {},
    "flags": null,
    "available_platforms": [
        "WEB",
        "MOBILE",
        "POS"
    ],
    "is_active": true,
    "is_notification_enabled": true,
    "customer_pay_ref": [
        220512063,
        220511959,
        220511991,
        220511992
    ],
    "created_at": "2025-07-29 09:13:51",
    "updated_at": "2025-07-29 09:13:51",
    "created_by": "admin"
}
```
