Payment API -- Create a Payment
1. Overview
This document provides developers with instructions for using a
fictional Payment API.

The Create Payment endpoint allows an application to initiate a payment
by submitting the required transaction details. The API accepts JSON
requests and returns the payment identifier, transaction status, amount,
and currency.

This is an independently created portfolio sample.
2. API Endpoint
- Endpoint: /v1/payments
- HTTP method: POST
- Content type: application/json
- Purpose: Creates a new payment request.
3. Authentication
The API uses a bearer token to authenticate requests.

Include this header in every API request:

Authorization: Bearer YOUR_API_TOKEN

Replace YOUR_API_TOKEN with a valid API access token.
4. Request Headers
Authorization
- Type: String
- Required: Yes
- Description: The API access token used to authenticate the
  request.
Content-Type
- Type: String
- Required: Yes
- Description: Specifies the format of the request body.
- Required value: application/json
5. Request Parameters
amount
- Type: Number
- Required: Yes
- Description: The amount to be charged.
- Example: 100.00
currency
- Type: String
- Required: Yes
- Description: The three-letter currency code for the payment.
- Example: EUR
description
- Type: String
- Required: No
- Description: A short description of the payment.
- Example: Order payment
6. Example Request
Send a POST request to /v1/payments with the following JSON body:
{
  "amount": 100.00,
  "currency": "EUR",
  "description": "Order payment"
}
7. Successful Response
When the request is accepted and processed successfully, the API returns
the payment details.

HTTP status: 200 OK

Example response:
{
  "payment_id": "pay_12345",
  "status": "successful",
  "amount": 100.00,
  "currency": "EUR"
}
Response Fields
payment_id
- Type: String
- Description: A unique identifier assigned to the payment.
status
- Type: String
- Description: The current status of the payment.
amount
- Type: Number
- Description: The amount submitted in the request.
currency
- Type: String
- Description: The currency used for the transaction.
8. Error Responses
The API may return the following errors if a request cannot be
processed.
400 -- Bad Request
The request contains missing, invalid, or incorrectly formatted
parameters. Check the request body and ensure all required fields are
included.
401 -- Unauthorized
The API access token is missing or invalid. Check the Authorization
header and provide a valid token.
500 -- Internal Server Error
An unexpected server-side error prevented the request from being
processed. Try again later. If the problem continues, contact the API
provider.
9. Example Error Response
{
  "error": {
    "code": "invalid_request",
    "message": "The payment amount must be greater than zero."
  }
}
10. Implementation Notes
- Ensure the payment amount is greater than zero.
- Use a valid three-letter currency code.
- Include the Authorization header in every request.
- Send the request body as JSON.
- Check the response status before treating a payment as successful.
- Handle error responses in your application.
## Disclaimer
This is a fictional API documentation sample created independently for
portfolio demonstration. The endpoint, authentication method, fields,
response examples, and status codes are illustrative. They do not
describe a real payment service or reproduce proprietary company
documentation.
