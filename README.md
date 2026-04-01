# Shopping_cart
class ShoppingCart:
    def __init__(self):
        self.items = {}  # store items as {name: [price, quantity]}

    def add_item(self, name, price, quantity):
        if name in self.items:
            self.items[name][1] += quantity  # update quantity
        else:
            self.items[name] = [price, quantity]
        print(f"{quantity}x {name} added.")

    def remove_item(self, name):
        if name in self.items:
            del self.items[name]
            print(f"{name} removed.")
        else:
            print("Item not found.")

    def view_cart(self):
        if not self.items:
            print("Cart is empty.")
            return

        print("\nYour Cart:")
        for name, (price, quantity) in self.items.items():
            print(f"{name} - ₱{price} x {quantity}")

    def get_total(self):
        total = sum(price * quantity for price, quantity in self.items.values())
        print(f"\nTotal: ₱{total}")


# --- Simple Menu ---
cart = ShoppingCart()

while True:
    print("\n1. Add Item")
    print("2. Remove Item")
    print("3. View Cart")
    print("4. Total")
    print("5. Exit")

    choice = input("Choose: ")

    if choice == "1":
        name = input("Item name: ")
        price = float(input("Price: "))
        quantity = int(input("Quantity: "))
        cart.add_item(name, price, quantity)

    elif choice == "2":
        name = input("Item name to remove: ")
        cart.remove_item(name)

    elif choice == "3":
        cart.view_cart()

    elif choice == "4":
        cart.get_total()

    elif choice == "5":
        print("Goodbye!")
        break

    else:
        print("Invalid choice.")
