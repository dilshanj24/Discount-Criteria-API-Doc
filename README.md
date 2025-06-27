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
  "discountName": "Sale 2023",
  "discountCode": "740003931",
  "discountCategory": 1,
  "discountEntity": 2,
  "attributes": {
    "season": "summer",
    "targetCustomers": "all"
  },
  "valueType": 1,
  "value": 15.00,
  "minimumEligibilityAmount": 100.00,
  "maximumEligibilityAmount": 1000.00,
  "validFrom": "2023-06-01 00:00:00",
  "validTo": "2023-08-31 23:59:59",
  "purchasingCriteria": [
    {
      "productId": 101,
      "minQuantity": 1
    },
    {
      "productId": 202,
      "minQuantity": 2
    }
  ],
  "benefitedProductList": [
    {
      "productId": 303,
      "discountPercentage": 10
    },
    {
      "productId": 404,
      "discountAmount": 5.00
    }
  ],
  "benefitedDiscount": 10.00,
  "notifications": true,
  "appliedPayIds": false,
  "createdBy": "admin"
}
```

### Response

```json
{
    "id": 1,
    "discountName": "Sale 2023",
    "discountCode": "740003931",
    "discountCategory": 1,
    "discountEntity": 2,
    "attributes": {
        "season": "summer",
        "targetCustomers": "all"
    },
    "valueType": 1,
    "value": 15.00,
    "minimumEligibilityAmount": 100.00,
    "maximumEligibilityAmount": 1000.00,
    "validFrom": "2023-06-01 00:00:00",
    "validTo": "2023-08-31 23:59:59",
    "purchasingCriteria": [
        {
            "productId": 101,
            "minQuantity": 1
        },
        {
            "productId": 202,
            "minQuantity": 2
        }
    ],
    "benefitedProductList": [
        {
            "productId": 303,
            "discountPercentage": 10
        },
        {
            "productId": 404,
            "discountAmount": 5.0
        }
    ],
    "benefitedDiscount": 10.00,
    "isActive": true,
    "notifications": true,
    "appliedPayIds": false,
    "createdAt": "2025-06-27 13:35:08",
    "updatedAt": "2025-06-27 13:35:08",
    "createdBy": "admin"
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
    "discountName": "Sale 2023",
    "discountCode": "740003931",
    "discountCategory": 1,
    "discountEntity": 2,
    "attributes": {
        "season": "summer",
        "targetCustomers": "all"
    },
    "valueType": 1,
    "value": 15.00,
    "minimumEligibilityAmount": 100.00,
    "maximumEligibilityAmount": 1000.00,
    "validFrom": "2023-06-01 00:00:00",
    "validTo": "2023-08-31 23:59:59",
    "purchasingCriteria": [
        {
            "productId": 101,
            "minQuantity": 1
        },
        {
            "productId": 202,
            "minQuantity": 2
        }
    ],
    "benefitedProductList": [
        {
            "productId": 303,
            "discountPercentage": 10
        },
        {
            "productId": 404,
            "discountAmount": 5.0
        }
    ],
    "benefitedDiscount": 10.00,
    "isActive": true,
    "notifications": true,
    "appliedPayIds": false,
    "createdAt": "2025-06-27 13:35:08",
    "updatedAt": "2025-06-27 13:35:08",
    "createdBy": "admin"
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
            "discountName": "Sale 2023",
            "discountCode": "740003931",
            "discountCategory": 1,
            "discountEntity": 2,
            "attributes": {
                "season": "summer",
                "targetCustomers": "all"
            },
            "valueType": 1,
            "value": 15.00,
            "minimumEligibilityAmount": 100.00,
            "maximumEligibilityAmount": 1000.00,
            "validFrom": "2023-06-01 00:00:00",
            "validTo": "2023-08-31 23:59:59",
            "purchasingCriteria": [
                {
                    "productId": 101,
                    "minQuantity": 1
                },
                {
                    "productId": 202,
                    "minQuantity": 2
                }
            ],
            "benefitedProductList": [
                {
                    "productId": 303,
                    "discountPercentage": 10
                },
                {
                    "productId": 404,
                    "discountAmount": 5.0
                }
            ],
            "benefitedDiscount": 10.00,
            "isActive": true,
            "notifications": true,
            "appliedPayIds": false,
            "createdAt": "2025-06-27 13:35:08",
            "updatedAt": "2025-06-27 13:35:08",
            "createdBy": "admin"
        },
        {
            "id": 2,
            "discountName": "December 2025",
            "discountCode": "740003934",
            "discountCategory": 1,
            "discountEntity": 2,
            "attributes": {
                "season": "summer",
                "targetCustomers": "all"
            },
            "valueType": 1,
            "value": 15.00,
            "minimumEligibilityAmount": 100.00,
            "maximumEligibilityAmount": 1000.00,
            "validFrom": "2023-06-01 00:00:00",
            "validTo": "2023-08-31 23:59:59",
            "purchasingCriteria": [
                {
                    "productId": 101,
                    "minQuantity": 1
                },
                {
                    "productId": 202,
                    "minQuantity": 2
                }
            ],
            "benefitedProductList": [
                {
                    "productId": 303,
                    "discountPercentage": 10
                },
                {
                    "productId": 404,
                    "discountAmount": 5.0
                }
            ],
            "benefitedDiscount": 10.00,
            "isActive": true,
            "notifications": true,
            "appliedPayIds": false,
            "createdAt": "2025-06-27 13:38:34",
            "updatedAt": "2025-06-27 13:38:34",
            "createdBy": "admin"
        }
    ],
    "page": 0,
    "size": 3,
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
    "id": 2,
    "discountName": "December 2025",
    "discountCode": "740003934",
    "discountCategory": 1,
    "discountEntity": 2,
    "attributes": {
        "season": "summer",
        "targetCustomers": "all"
    },
    "valueType": 1,
    "value": 15.00,
    "minimumEligibilityAmount": 100.00,
    "maximumEligibilityAmount": 1000.00,
    "validFrom": "2023-06-01 00:00:00",
    "validTo": "2023-08-31 23:59:59",
    "purchasingCriteria": [
        {
            "productId": 101,
            "minQuantity": 1
        },
        {
            "productId": 202,
            "minQuantity": 2
        }
    ],
    "benefitedProductList": [
        {
            "productId": 303,
            "discountPercentage": 10
        },
        {
            "productId": 404,
            "discountAmount": 5.0
        }
    ],
    "benefitedDiscount": 10.00,
    "isActive": false,
    "notifications": true,
    "appliedPayIds": false,
    "createdAt": "2025-06-27 13:38:34",
    "updatedAt": "2025-06-27 13:38:34",
    "createdBy": "admin"
}
```
