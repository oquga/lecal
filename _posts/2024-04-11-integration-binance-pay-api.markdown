---
layout: post
date: 2024-04-08 12:00:00 +0200
title: "Integration with Binance Pay API"
---

# Overview of Binance Pay API Integration

LeadsCalendar integrates with the Binance Pay API to enable cryptocurrency payment processing within the application. The Binance Pay API provides functionalities for creating payment requests, handling transactions, and managing merchant accounts.

# Steps to Set Up a Binance Developer Account and Obtain API Credentials

To integrate LeadsCalendar with the Binance Pay API and obtain API credentials, follow these steps:

1. **Create a Binance Developer Account:**
   - Go to the [Binance Developer Portal](https://developers.binance.com/).
   - Sign up for a developer account if you don't have one already.
   - Log in to the developer dashboard.

2. **Create an API Key:**
   - In the developer dashboard, navigate to "API Management" > "Create New API Key."
   - Provide a name for your API key and select the appropriate permissions (e.g., trading, wallet).
   - Generate and note down the API key and secret provided by Binance.

3. **Configure `.env` File:**
   - Create a `.env` file in the root directory of your LeadsCalendar project.
   - Add the Binance API key and secret to the `.env` file as follows:
     ```plaintext
     BINANCE_PAY_API_KEY=your_binance_api_key
     BINANCE_PAY_API_SECRET=your_binance_api_secret
     ```

# Code Samples for Processing Cryptocurrency Payments through Binance Pay

Here's an example code snippet in Ruby using the `binance-ruby` gem to process cryptocurrency payments through Binance Pay within LeadsCalendar:

```ruby
require 'binance-ruby'

# Initialize Binance client
client = Binance::Client.new(
  api_key: ENV['BINANCE_PAY_API_KEY'],
  secret_key: ENV['BINANCE_PAY_API_SECRET']
)

# Create payment request
response = client.create_binance_pay_order(
  coin: 'BTC',
  amount: 0.001, # Amount in BTC
  recvWindow: 5000,
  timestamp: Time.now.to_i * 1000
)

if response['code'] == 0
  payment_url = response['data']['url']
  # Redirect the user to payment_url for cryptocurrency payment
else
  # Handle payment request creation error
  puts response['msg']
end



