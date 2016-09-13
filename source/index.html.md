---
title: MusicApp API Docs

language_tabs:
- shell: cURL
- ruby: Ruby
- php: PHP
- javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>
  - <a href='https://github.com/acme'>Client libraries</a>


includes:
  - errors

search: true
---

# Draft Orders

The Draft Orders API makes it possible to retrieve and create a draft order via the API. Additionally, using this API, it is possible to create an order on which taxes and all total amounts are calculated automatically by Shopify.

For more information, see our guide (link).

## The draft orders object

Attributes | Description |
---------- | ------- |
`id`<br>*integer*</br> | The `id` of the draft order.
`order_id`<br>*integer*</br> | The `id` of the order associated to the draft order, once created.
`name`<br>*string*</br> | Name of the draft order.<br> **format:** *#D<number>*, where *number* is an sequential identifier unique to the shop, starting at 1. For example, #D133
`customer`<br>*object*</br> | Customer object (link to customer object definition)
`shipping_address`<br>*object*</br> | The mailing address to where the draft order will be shipped. (link)
`billing_address`<br>*object*</br> | The mailing address associated with the payment method. (link)
`note`<br>*string*</br> | The text of an optional note that a shop owner can attach to the draft order.
`email`<br>*string*</br> | The email address used for sending notifications.
`currency`<br>*string*</br> | The three letter code for the currency to be used for the payment.
`invoices_sent_at`<br>*dateTime*</br> | DateTime when the invoice was emailed to the customer by Shopify.
`invoice_url`<br>*string*</br> | The url to send to the customer so that they can complete the checkout.  When using `send_invoice`, this url is emailed to the customer. This field can be used so that an API client can use another method of communication to provide the url to the customer.
`line_items[]`<br>*array of line items*</br> | Link to table below
`metafields[]`<br>*array of metafields*</br> | Link to table below
`shipping_line` <br>*object*</br> | shipping_line object
`tags`<br>*string of csv*</br> | Tags are additional short descriptors, commonly used for filtering and searching, formatted as a string of comma-separated values. Each individual tag is limited to 40 characters in length.
`tax_exempt`<br>*boolean*</br> | Sets whether taxes are exempt for this draft order. If this value is false, Shopify will honor the `tax_exempt` value for each `line_item`.
`tax_lines[]`<br>*array of tax line sums*</br> | Tax lines describing the sum of each type of tax line for line items and shipping line.
`total_weight`<br>*integer*</br> | The weight of all the line items.
`discount`<br>*boolean*</br> | Order level discount.
`total_line_items_price`<br>*integer*</br> | Subtotal before order-level discounts, shipping and taxes have been applied
`total_shipping_price`<br>*integer*</br> | Total cost of shipping
`total_tax`<br>*integer*</br> | Total tax amount
`subtotal_price`<br>*integer*</br> | Subtotal after discounts, before shipping and taxes have been applied
`total_price`<br>*integer*</br> | Includes discounts, shipping and taxes
`completed_at`<br>*dateTime*</br> | Date at which an order was created and the draft order moved to “completed” status.
`created_at`<br>*dateTime*</br> | Date at which an order was created.
`updated_at`<br>*dateTime*</br> | Date at which an order was updated.
`status`<br>*dateTime*</br> | String describing the state of the draft order: `open`, `invoice sent`, `completed`.


## Get /admin/draft_orders.json

```ruby
require 'music'

api = Music::APIClient.authorize!('your-api-key')
api.albums.get
```

```shell
curl "http://example.com/api/albums"
  -H "Authorization: your-api-key"
```

```php
$client = new Acme\Music\Client('your-api-key');
$client->authorize();
$albums = $client->getAlbums();
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "title": "Dubnobasswithmyheadman",
    "breed": "Underworld",
    "artist": Underworld,
    "year": 1994
  },
  {
    "id": 2,
    "title": "ISDN",
    "artist": "unknown",
    "year": 1994
  }
]
```

Retrieve a list of all Draft Orders.

This is a good place to call out dependencies with other API calls (order etc.) and link to additional guides ad tutorials to view sequence diagrams, flows, and more detailed use-case based information.

### HTTP Request

`GET admin/draft_orders.json`

### Query Parameters

Parameter | Description |
--------- | ------- |
`field`<br>*optional, by default returns all fields*</br> | Comma-separated list of fields to include in the response.
`limit`<br>*optional, default 50, max 250*</br> | Filter page size.
`page`<br>*optional*</br> | Display a specific page.
`since_id`<br>*optional*</br> | Restrict results to be after given ID
`status`<br>*optional*</br> | Filter by status.  Possible values: `open`,`invoice_sent`,`completed`
`ids`<br>*optional*</br> | Filter by list of `ids`

<aside class="success">
Get all the things!
</aside>

### Returns ###

Returns an array of `draft_orders` objects formatted as JSON.
