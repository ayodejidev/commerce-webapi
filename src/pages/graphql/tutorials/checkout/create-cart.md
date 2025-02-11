---
title: Step 2. Create an empty cart
description: Learn how to create a cart with the GraphQL API.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
keywords:
  - GraphQL
  - Checkout
---

# Step 2. Create an empty cart

The procedure for creating a cart varies for logged-in customers and guests.

The `customerCart` query returns the active cart for the logged-in customer. If the cart does not exist, the query creates one. You must specify the customer's authorization token in the headers. Otherwise, the query fails. ["Get customer authorization token"](../../usage/authorization-tokens.md) describes these tokens.

For guests, use the [`createGuestCart`](../../schema/cart/mutations/create-guest-cart.md) mutation to create an empty shopping cart and generate a cart ID for a guest user. If the guest later logs in as a customer, use the [`mergeCarts`](../../schema/cart/mutations/merge.md) mutation to transfer the contents of the guest cart into the customer's cart.

## Create a customer cart

The customer created in the previous step does not have an active cart. The following query creates an empty cart and returns the cart ID. You must specify the customer's authorization token in the headers of the call.

**Request:**

```graphql
{
  customerCart{
    id
  }
}
```

**Response:**

```json
{
  "data": {
    "customerCart": {
      "id": "pXVxnNg4PFcK1lD60O5evqF7f4SkiRR1"
    }
  }
}
```

In the subsequent tutorial steps, the unique shopping cart identifier `pXVxnNg4PFcK1lD60O5evqF7f4SkiRR1` will be listed as `{ CART_ID }`.
Copy the value of the id attribute. Use this value in subsequent steps wherever the { CART_ID } variable is specified.

## Create a guest cart

The following example creates an empty cart for a guest. Do not include an authorization token on any call made on behalf of a guest.

**Request:**

```graphql
mutation {
  createGuestCart {
      cart {
          id
      }
  }
}
```

**Response:**

```json
{
  "data": {
    "createGuestCart": {
      "cart": {
        "id": "A7jCcOmUjjCh7MxDIzu1SeqdqETqEa5h"
      }
    }
  }
}
```

In the subsequent tutorial steps, the unique shopping cart identifier `A7jCcOmUjjCh7MxDIzu1SeqdqETqEa5h` will be listed as `{ CART_ID }`.
Copy the value of the id attribute. Use this value in subsequent steps wherever the { CART_ID } variable is specified.

## Verify this step

There are no additional verification steps. The value of `id` is not displayed on the website or in the Admin.
