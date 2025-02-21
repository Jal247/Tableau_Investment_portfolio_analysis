When an investment firm provides portfolio details, they typically include static details (recorded at the time of investment) and dynamic details (which update periodically, often via APIs).



2. Dynamic Data (Fetched via API)
To update the current asset value, we integrate APIs such as:

Stock Market API (Yahoo Finance, Alpha Vantage, IEX Cloud) → for real-time stock prices
Cryptocurrency API (CoinGecko, Binance API) → for live crypto prices
Gold API (Metals-API) → for live gold rates
Real Estate API (Zillow, Realtor API) → for property valuations
3. API Integration


import requests
import random

# Mock API Endpoints (Replace with real API URLs)
STOCK_API_URL = "https://api.example.com/stocks"
CRYPTO_API_URL = "https://api.example.com/crypto"
GOLD_API_URL = "https://api.example.com/gold"
REAL_ESTATE_API_URL = "https://api.example.com/real_estate"

# Sample function to fetch asset values
def fetch_asset_value(asset_type):
    if asset_type == "Stocks":
        response = requests.get(STOCK_API_URL, params={"symbol": "AAPL"})  # Example stock
    elif asset_type == "Crypto":
        response = requests.get(CRYPTO_API_URL, params={"symbol": "BTC"})  # Bitcoin
    elif asset_type == "Gold":
        response = requests.get(GOLD_API_URL)
    elif asset_type == "Real Estate":
        response = requests.get(REAL_ESTATE_API_URL, params={"location": "Toronto"})
    elif asset_type == "Bonds":
        return round(random.uniform(0.98, 1.05) * 100, 2)  # Mock bond value multiplier
    else:
        return None

    if response.status_code == 200:
        return response.json().get("current_price", None)  # Extracting current price
    else:
        return None

# Fetch and update current asset values
customer_portfolio = [
    {"Customer_ID": 101, "Asset_Type": "Stocks"},
    {"Customer_ID": 102, "Asset_Type": "Crypto"},
    {"Customer_ID": 103, "Asset_Type": "Real Estate"},
    {"Customer_ID": 104, "Asset_Type": "Stocks"},
    {"Customer_ID": 105, "Asset_Type": "Bonds"},
]

for customer in customer_portfolio:
    asset_value = fetch_asset_value(customer["Asset_Type"])
    print(f"Customer {customer['Customer_ID']} - {customer['Asset_Type']}: ${asset_value}")

