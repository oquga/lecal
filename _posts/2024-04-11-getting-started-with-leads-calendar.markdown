---
layout: post
date: 2024-04-10 12:00:00 +0200
title: "Getting Started with LeadsCalendar"
---

## Installation Instructions

To set up LeadsCalendar locally for development, follow these steps:

1 Clone the LeadsCalendar repository from GitHub:
================================================
git clone https://github.com/yourusername/leads-calendar.git


2 Navigate to the project directory:
================================================
cd leads-calendar


3 Install dependencies using Bundler:
================================================
bundle install

4 Create a `.env` file in the root directory and add your API keys and credentials:
================================================
GOOGLE_CALENDAR_API_KEY=your_google_calendar_api_key
PAYPAL_CLIENT_ID=your_paypal_client_id
PAYPAL_SECRET=your_paypal_secret
BINANCE_PAY_API_KEY=your_binance_pay_api_key


5 Configuration Steps for API Keys and Credentials
================================================


5.1 Google Calendar API:
   - Follow the guide at [Google Calendar API Quickstart](https://developers.google.com/calendar/api/quickstart) to obtain your API key.
   - Add the API key to the `.env` file as `GOOGLE_CALENDAR_API_KEY`.


5.2 PayPal REST API:
   - Sign up for a PayPal developer account and create an application to obtain your client ID and secret.
   - Add the client ID and secret to the `.env` file as `PAYPAL_CLIENT_ID` and `PAYPAL_SECRET`.


5.3 Binance Pay API:
   - Register for a Binance developer account and generate an API key.
   - Add the API key to the `.env` file as `BINANCE_PAY_API_KEY`.
