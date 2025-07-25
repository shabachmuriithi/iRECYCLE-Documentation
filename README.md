#iRECYCLE app documentation

Welcome to iRECYCLE app documentation. This is an app that helps second-hand clothes traders to recycle textile waste by connecting them to recycling companies.

##Table of Contents

-User Guide -Developer Guide -FAQ

##Overview The iRECYCLE app facilitates recycling of textile waste in Kenya, targeting second-hand clothes traders within Nairobi and its environs. The goal of this application is to contribute to environmental sustainability especially by reducing the waste that ends up at the Dandora dumpsite from unsold second-hand clothes.


iRECYCLE User Guide
For traders: Getting started

This will serve as a guide for the traders using iRECYCLE app to recycle textile waste.
1. Download the app

The app will be available for download to select traders for testing via a link that will be provided.
2. Create an account

Open the app and click "sign up" Enter your name, phone number, location, and password. Click on 'Sign Up,' and your account is created.

If you already have an account, log in with your phone number and password.
3. Request a pickup

On the home page, tap on the new pick-up request. On this page, fill in: -Type of textile from the list of materials provided. -Estimated weight -Add a photo (tap "Upload") of the materials being uploaded.

Tap "submit" to send your request. PS: You will receive a notification once your pickup has been scheduled.
4. View price catalogue

On the price catalogue screen, you will see the different types of material we recycle and their current price per kilogram. This will be helpful when planning your pickups, so that you know how much to expect from your uploaded pending pickups.
5 . View pickup history

Here you will see the past and pending pickups. This will enable you to track your past deliveries and organize your pickups. You will see the date of a particular pickup, the weight, and its status. Type of textile Estimated weight Add a photo (tap "Upload")
6. Track payment history

Here you will see the date, the amounts, and the status of your payments. For past pickups, the payment will be marked as complete, for pending and scheduled pickuos the payment will be pending. This will help you track whether your pickups correlate
with your payments.
7. Manage your profile

Here, you will update your profile to match your current status Update your name, phone number and the current market; save to update your profile.

For agents: Getting started This will serve as a guide for agents collecting textile waste from traders.
1. Download the app

Traders will get a link to download the app
2. Create an account and log in

On the Sign Up screen, enter: Name Phone number Password Confirm password

Tap "Sign Up" to create your account.

On the login screen: Enter your phone number and password, and log in to access the app.
3. View collections

On the home page, click on View Collections, here, you will see the traders in your assigned markets who have pending pickups and the details of the pickups. You will see a map that will direct you to the traders' exact location in the market
4. Price catalogue

Here you will see the buying rate of the different types of materials, which you will use to guide on the amount that a trader is supposed to pay.
5. Request payment

Once you have completed a pickup from a trader, request payment by entering the trader's phone number and sending a payment request to the recycling company that completes the payment.
6. Pickup history.

Here you will see the collection history from your assigned market. This history will contain the date and the type of the material and the weight of the material and the name of the trader from whom the collection was made.
7.

This guide is for developers building the iRecycle app using Android Studio (mobile), React (dashboard), and Django REST Framework (APIs). It covers setup, API integration, testing, and troubleshooting.

Table of Contents

    System Requirements

    Project Setup

    API Integration

    Testing

    System Requirements Hardware: Minimum 8GB RAM

Software: Android Studio 2022.3+ (with Android SDK). npm for React. Python 3.8+, Django 4.2+, Django REST Framework 3.14+. PostgreSQL 13+. Postman for API testing.

Dependencies: Install via pip install django djangorestframework and npm install.

    Project Setup 2.1 Android App (Android Studio) Clone the repo: git clone git@github.com:akirachix/imperial-mobile.git Open Android Studio, select "Open an existing project." Configure the emulator. Sync Gradle and build the project.

2.2 React Dashboard Navigate to the dashboard folder: clone and cd git@github.com:akirachix/imperial-frontend.git Install dependencies: npm install Start development server: npm start (runs on http://localhost:3000).

2.3 Django Backend Navigate to the backend folder: clone and cd git@github.com:akirachix/imperial_backend.git Create a virtual environment: python -m venv venv Activate it: source venv/bin/activate Install requirements: pip install -r requirements.txt Apply migrations: python manage.py migrate Run server: python manage.py runserver (runs on http://localhost:8000)

    API Integration 3.1 Available APIs

The following serializers define the API endpoints using Django REST Framework: TraderSerializer:Model: Trader Fields: All (all) Endpoint: /api/traders/ Use: Manage trader profiles.

AgentSerializer:Model: Agent Fields: All (all) Endpoint: /api/agents/ Use: Manage agent details.

RecyclingCompanySerializer:Model: RecyclingCompany Fields: All (all) Endpoint: /api/companies/ Use: Manage company data.

UserUnionSerializer:Fields: first_name, last_name, phone_number, user_type Endpoint: /api/user-union/ Use: Unified user creation.

PaymentSerializer:Model: Payment Fields: All (all) Endpoint: /api/payments/ Use: Track payment transactions.

STKPushSerializer:Fields: phone_number, amount, order_item, account_reference, transaction_desc Endpoint: /api/stk-push/ Use: Initiate M-Pesa STK push payments.

DarajaAPISerializer:Model: Payment Fields: All (all) Endpoint: /api/daraja/ Use: Integrate with M-Pesa Daraja API.

FabricCatalogueSerializer:Model: FabricCatalogue Fields: All (all) Endpoint: /api/catalogue/ Use: Manage fabric listings.

CollectionSerializer:Model: Collection Fields: All (all) Endpoint: /api/collections/ Use: Track collection data.

ClothesListingSerializer:Model: ClothesListing Fields: All (all) Endpoint: /api/clothes-listings/ Use: Manage cloth listings.

MarketSerializer:Model: Market Fields: All (all) Endpoint: /api/markets/ Use: Manage market locations.

3.2 M-Pesa Integration

Use DarajaAPI for authentication and payment requests. Payload (STK Push):json { "phone_number": "254712345678", "amount": "1000.00", "order_item": ["Textile Waste"], "account_reference": "TX12345", "transaction_desc": "Payment for pickup" }

Endpoint: POST /api/stk-push/ Secure with OAuth 2.0 (consumer key/secret from Safaricom).

3.3 Connecting Frontend Android: Use Retrofit to call APIs (e.g., /api/traders/). React: Use axios or fetch to connect to /api/payments/ for dashboard data.

    Testing 4.1 Postman Testing Import API endpoints into Postman. Test GET /api/traders/ and POST /api/stk-push/ with sample data. Save requests

4.2 PyTest for Django Install PyTest: pip install pytest Write tests in tests/ folder (test_api.py) python def test_trader_serializer(): data = {"first_name": "John", "phone_number": "254712345678"} serializer = TraderSerializer(data=data) assert serializer.is_valid()

Run tests: pytest


