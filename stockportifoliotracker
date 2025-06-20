import csv

# Hardcoded stock prices in INR
STOCK_PRICES_INR = {
    'AAPL': 14551.56,
    'GOOGL': 11242.35,
    'MSFT': 27399.96,
    'AMZN': 12090.61,
    'TSLA': 14130.75,
    'META': 29123.87,
    'NVDA': 37391.50,
    'NFLX': 39902.25,
    'RELIANCE': 2850.00,
    'TCS': 3850.00,
    'HDFCBANK': 1650.00,
    'INFY': 1500.00
}

portfolio = []
total_value = 0

print("📈 Stock Portfolio Tracker (INR)")
print("Type 'done' when you are finished entering stocks.\n")

while True:
    stock = input("Enter stock symbol (e.g., AAPL, RELIANCE): ").upper()
    if stock == "DONE":
        break
    if stock not in STOCK_PRICES_INR:
        print("❌ Stock not found in our database. Try again.")
        continue

    try:
        quantity = int(input(f"Enter quantity of {stock}: "))
        if quantity <= 0:
            print("❌ Quantity must be a positive number.")
            continue
    except ValueError:
        print("❌ Please enter a valid number.")
        continue

    price = STOCK_PRICES_INR[stock]
    value = quantity * price
    portfolio.append({"name": stock, "quantity": quantity, "value": value})
    total_value += value

    print(f"✅ Added {quantity} shares of {stock} worth ₹{value:.2f}\n")

# Display Portfolio Summary
print("\n📊 Portfolio Summary:")
print("-" * 40)
for item in portfolio:
    print(f"{item['name']}: {item['quantity']} shares × ₹{STOCK_PRICES_INR[item['name']]:.2f} = ₹{item['value']:.2f}")
print("-" * 40)
print(f"Total Portfolio Value: ₹{total_value:.2f}")

# Save to CSV
save = input("\nDo you want to download your portfolio as CSV? (yes/no): ").lower()
if save == "yes":
    with open("portfolio.csv", "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["Stock", "Quantity", "Value (₹)"])
        for item in portfolio:
            writer.writerow([item['name'], item['quantity'], f"₹{item['value']:.2f}"])
        writer.writerow([])
        writer.writerow(["Total Value", f"₹{total_value:.2f}"])
    print("✅ Portfolio saved as 'portfolio.csv'.")
else:
    print("📝 Portfolio not saved.")
