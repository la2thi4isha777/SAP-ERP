# Simple ERP Inventory Management System

class Product:
    def __init__(self, product_id, name, quantity, reorder_level):
        self.product_id = product_id
        self.name = name
        self.quantity = quantity
        self.reorder_level = reorder_level

    def update_quantity(self, qty):
        self.quantity += qty
        print(f"✅ Inventory updated for {self.name}. New quantity: {self.quantity}")

    def check_reorder(self):
        if self.quantity <= self.reorder_level:
            print(f"⚠️ Reorder Alert: {self.name} stock is low (Current: {self.quantity})")
        else:
            print(f"✅ {self.name} stock is sufficient (Current: {self.quantity})")


# Inventory Dictionary
inventory = {}

# Add product
def add_product(product_id, name, quantity, reorder_level):
    if product_id in inventory:
        print("❌ Product ID already exists.")
    else:
        inventory[product_id] = Product(product_id, name, quantity, reorder_level)
        print(f"✅ Product '{name}' added successfully.")

# Update product quantity
def update_product(product_id, qty):
    if product_id in inventory:
        inventory[product_id].update_quantity(qty)
    else:
        print("❌ Product not found.")

# Generate stock report
def stock_report():
    print("\n📦 Inventory Stock Report")
    print("-" * 40)
    for p in inventory.values():
        print(f"{p.product_id} | {p.name} | Qty: {p.quantity} | Reorder Level: {p.reorder_level}")
    print("-" * 40)

# Check all reorder alerts
def check_reorders():
    print("\n🔍 Reorder Check")
    for p in inventory.values():
        p.check_reorder()

# Sample Usage
add_product(101, "Industrial Drill", 20, 5)
add_product(102, "Steel Bolts", 50, 10)
add_product(103, "Hydraulic Pump", 5, 3)

update_product(101, -18)
update_product(102, -45)

stock_report()
check_reorders()

