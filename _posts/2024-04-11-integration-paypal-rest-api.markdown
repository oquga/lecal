---
layout: post
date: 2024-04-07 12:00:00 +0200
title: "Integration with PayPal REST API"
---

# Overview of PayPal REST API Integration

LeadsCalendar integrates with the PayPal REST API to facilitate payment processing within the application. The PayPal REST API offers a range of features for processing payments, managing transactions, and handling subscriptions.

# Steps to Set Up a PayPal Developer Account and Obtain API Credentials

To integrate LeadsCalendar with the PayPal REST API and obtain API credentials, follow these steps:

1. **Create a PayPal Developer Account:**
   - Go to the [PayPal Developer Portal](https://developer.paypal.com/).
   - Sign up for a developer account if you don't have one already.
   - Log in to the developer dashboard.

2. **Create a REST API App:**
   - In the developer dashboard, navigate to "My Apps & Credentials."
   - Click on "Create App" under the REST API apps section.
   - Provide a name for your app and select the appropriate sandbox or live environment.
   - Generate and note down the client ID and secret provided by PayPal.

3. **Configure `.env` File:**
   - Create a `.env` file in the root directory of your LeadsCalendar project.
   - Add the PayPal client ID and secret to the `.env` file as follows:
     ```plaintext
     PAYPAL_CLIENT_ID=your_paypal_client_id
     PAYPAL_CLIENT_SECRET=your_paypal_client_secret
     ```

# Code Samples for Processing Payments through PayPal

Here's an example code snippet in Ruby using the `paypal-sdk-rest` gem to process payments through PayPal within LeadsCalendar:

```ruby
require 'paypal-sdk-rest'

# Initialize PayPal client
PayPal::SDK::REST.set_config(
  mode: 'sandbox', # or 'live' for production
  client_id: ENV['PAYPAL_CLIENT_ID'],
  client_secret: ENV['PAYPAL_CLIENT_SECRET']
)

# Create payment
payment = PayPal::SDK::REST::Payment.new({
  intent: 'sale',
  payer: {
    payment_method: 'paypal'
  },
  transactions: [{
    amount: {
      total: '1.00',
      currency: 'USD'
    },
    description: 'Event Payment'
  }],
  redirect_urls: {
    return_url: 'http://localhost:4000/payment/success',
    cancel_url: 'http://localhost:4000/payment/cancel'
  }
})

# Execute payment
if payment.create
  approval_url = payment.links.find { |link| link.rel == 'approval_url' }.href
  # Redirect the user to approval_url for payment approval
else
  # Handle payment creation error
  puts payment.error.inspect
end



