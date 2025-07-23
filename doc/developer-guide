This guide is for developers building the iRecycle app using Android Studio (mobile), React (dashboard), and Django REST Framework (APIs). 
It covers setup, API integration, testing, and troubleshooting.

Table of Contents
1. System Requirements 
2. Project Setup 
3. API Integration 
4. Testing 
 

1. System Requirements
Hardware: 
Minimum 8GB RAM
  
Software:
Android Studio 2022.3+ (with Android SDK).
npm for React.
Python 3.8+, Django 4.2+, Django REST Framework 3.14+.
PostgreSQL 13+.
Postman for API testing.

Dependencies: Install via pip install django djangorestframework and npm install.

2. Project Setup
2.1 Android App (Android Studio)
Clone the repo: git clone git@github.com:akirachix/imperial-mobile.git
Open Android Studio, select "Open an existing project."
Configure the emulator.
Sync Gradle and build the project.

2.2 React Dashboard
Navigate to the dashboard folder: clone and cd git@github.com:akirachix/imperial-frontend.git
Install dependencies: npm install
Start development server: npm start (runs on http://localhost:3000).

2.3 Django Backend
Navigate to the backend folder: clone and cd git@github.com:akirachix/imperial_backend.git
Create a virtual environment: python -m venv venv
Activate it: source venv/bin/activate 
Install requirements: pip install -r requirements.txt
Apply migrations: python manage.py migrate
Run server: python manage.py runserver (runs on http://localhost:8000)



3. API Integration
3.1 Available APIs
                                        
The following serializers define the API endpoints using Django REST Framework:
TraderSerializer:Model: Trader
Fields: All (__all__)
Endpoint: /api/traders/
Use: Manage trader profiles.

AgentSerializer:Model: Agent
Fields: All (__all__)
Endpoint: /api/agents/
Use: Manage agent details.

RecyclingCompanySerializer:Model: RecyclingCompany
Fields: All (__all__)
Endpoint: /api/companies/
Use: Manage company data.

UserUnionSerializer:Fields: first_name, last_name, phone_number, user_type
Endpoint: /api/user-union/
Use: Unified user creation.

PaymentSerializer:Model: Payment
Fields: All (__all__)
Endpoint: /api/payments/
Use: Track payment transactions.

STKPushSerializer:Fields: phone_number, amount, order_item, account_reference, transaction_desc
Endpoint: /api/stk-push/
Use: Initiate M-Pesa STK push payments.

DarajaAPISerializer:Model: Payment
Fields: All (__all__)
Endpoint: /api/daraja/
Use: Integrate with M-Pesa Daraja API.

FabricCatalogueSerializer:Model: FabricCatalogue
Fields: All (__all__)
Endpoint: /api/catalogue/
Use: Manage fabric listings.

CollectionSerializer:Model: Collection
Fields: All (__all__)
Endpoint: /api/collections/
Use: Track collection data.

ClothesListingSerializer:Model: ClothesListing
Fields: All (__all__)
Endpoint: /api/clothes-listings/
Use: Manage cloth listings.

MarketSerializer:Model: Market
Fields: All (__all__)
Endpoint: /api/markets/
Use: Manage market locations.

3.2 M-Pesa Integration
                                        
Use DarajaAPI for authentication and payment requests.
Payload (STK Push):json
{
  "phone_number": "254712345678",
  "amount": "1000.00",
  "order_item": ["Textile Waste"],
  "account_reference": "TX12345",
  "transaction_desc": "Payment for pickup"
}
                                        
Endpoint: POST /api/stk-push/
Secure with OAuth 2.0 (consumer key/secret from Safaricom).

3.3 Connecting Frontend
Android: Use Retrofit to call APIs (e.g., /api/traders/).
React: Use axios or fetch to connect to /api/payments/ for dashboard data.

4. Testing
4.1 Postman Testing
Import API endpoints into Postman.
Test GET /api/traders/ and POST /api/stk-push/ with sample data.
Save requests 

4.2 PyTest for Django
Install PyTest: pip install pytest
Write tests in tests/ folder (test_api.py)
python
def test_trader_serializer():
    data = {"first_name": "John", "phone_number": "254712345678"}
    serializer = TraderSerializer(data=data)
    assert serializer.is_valid()

Run tests: pytest






  


