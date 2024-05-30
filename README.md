# Coffee Machine Program

## Overview
This Coffee Machine program is a command-line application written in Python using Object-Oriented Programming (OOP) principles. The program simulates a coffee vending machine, allowing users to select from different types of coffee, manage resources, process payments, and generate reports. This version of the program is an improvement over a previous procedural implementation, leveraging the benefits of OOP for better organization, scalability, and maintainability.

## Author
Onyedika Joel Chukwuka

## Features
- **Select Coffee**: Users can choose from various coffee options provided by the `Menu` class.
- **Resource Management**: The `CoffeeMaker` class checks and manages the resources (water, milk, coffee).
- **Payment Processing**: The `MoneyMachine` class handles the calculation and verification of payments.
- **Reports**: Users can request reports on the current resources and total profit.
- **Machine Control**: Users can turn off the machine.

## Classes and Their Responsibilities

### Menu
- **Methods**:
  - `get_items()`: Returns a string of available coffee options.
  - `find_drink(order_name)`: Returns a `MenuItem` object corresponding to the selected coffee.

### MenuItem
- Represents a coffee option with its name, cost, and required ingredients.

### CoffeeMaker
- **Methods**:
  - `report()`: Prints the current resource levels.
  - `is_resource_sufficient(drink)`: Checks if there are enough resources to make the selected coffee.
  - `make_coffee(order)`: Deducts the required ingredients from the resources and simulates making coffee.

### MoneyMachine
- **Methods**:
  - `report()`: Prints the current money status.
  - `make_payment(cost)`: Processes the coins inserted by the user and verifies if the payment is sufficient.

## Code Explanation
```python
from menu import Menu, MenuItem
from coffee_maker import CoffeeMaker
from money_machine import MoneyMachine

money_machine = MoneyMachine()
coffee_maker = CoffeeMaker()
menu = Menu()

is_on = True

while is_on:
    options = menu.get_items()
    choice = input(f"What would you like? ({options}): ")
    if choice == "off":
        is_on = False
    elif choice == "report":
        coffee_maker.report()
        money_machine.report()
    else:
        drink = menu.find_drink(choice)
        if coffee_maker.is_resource_sufficient(drink) and money_machine.make_payment(drink.cost):
            coffee_maker.make_coffee(drink)
```
### Main Loop
1. **Initialize Objects**:
   - `money_machine`: Instance of `MoneyMachine`.
   - `coffee_maker`: Instance of `CoffeeMaker`.
   - `menu`: Instance of `Menu`.

2. **Main Loop**:
   - The machine runs in a loop until `is_on` is set to `False`.
   - Prompts the user to choose an action: `off`, `report`, or a coffee option.
   - If `off` is selected, the loop terminates, turning off the machine.
   - If `report` is selected, the machine prints the current resource and money status.
   - For coffee options, the program:
     - Finds the selected drink from the menu.
     - Checks if there are enough resources to make the drink.
     - Processes the payment.
     - If resources and payment are sufficient, it makes the coffee.

## Usage
1. Run the program.
2. Choose an action: `espresso`, `latte`, `cappuccino`, `report`, or `off`.
3. Follow the prompts to insert coins and complete the transaction.
4. Enjoy your coffee!

Feel free to drop your comments!
