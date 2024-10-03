# floristics# Define available flowers and their prices
flowers = {
    "Roses": 2.50,
    "Tulips": 1.50,
    "Lilies": 3.00,
    "Sunflowers": 2.00,
    "Daisies": 1.25
}

# Function to display available flowers
def display_flowers():
    print("Welcome to the Floristry Shop!")
    print("Here are the flowers we have available:")
    for flower, price in flowers.items():
        print(f"{flower}: ${price:.2f} per stem")

# Function to take the order
def take_order():
    order = {}
    while True:
        choice = input("Which flower would you like to buy? (or type 'done' to finish): ").capitalize()
        if choice == "Done":
            break
        elif choice in flowers:
            quantity = int(input(f"How many {choice}s would you like? "))
            if choice in order:
                order[choice] += quantity
            else:
                order[choice] = quantity
        else:
            print("Sorry, we don't have that flower. Please choose from the available list.")

    return order

# Function to calculate the total cost
def calculate_total(order):
    total_cost = 0
    print("\nYour order summary:")
    for flower, quantity in order.items():
        cost = flowers[flower] * quantity
        total_cost += cost
        print(f"{quantity} x {flower} = ${cost:.2f}")

    print(f"Total cost: ${total_cost:.2f}")
    return total_cost

# Main function to run the shop
def floristry_shop():
    display_flowers()
    order = take_order()
    if order:
        calculate_total(order)
    else:
        print("No order was placed.")

# Run the floristry shop simulation
floristry_shop()
