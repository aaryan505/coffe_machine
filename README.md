# coffe_machine
# Coffee Machine Program

This repository contains a simulation of a coffee machine that can serve various types of coffee. It is an interactive program where users can select a drink, check the machine's status, and manage resources.

## Table of Contents
- [Features](#features)
- [Modules](#modules)
- [How to Run](#how-to-run)
- [Usage](#usage)
- [Example Session](#example-session)
- [Contributing](#contributing)
- [License](#license)

## Features
- Select from a menu of drinks: espresso, latte, cappuccino.
- Check the machine's resource status.
- Process payments.
- Make coffee if resources and payment are sufficient.
- Turn off the machine.

## Modules
The program is divided into several modules:
- `menu.py`: Contains the `Menu` and `MenuItem` classes, which manage the drink options.
- `coffee_maker.py`: Contains the `CoffeeMaker` class, which manages the machine's resources and coffee-making process.
- `money_machine.py`: Contains the `MoneyMachine` class, which handles payment processing.

## How to Run
1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/coffee-machine.git
    cd coffee-machine
    ```

2. Make sure you have the necessary modules (`Menu`, `MenuItem`, `CoffeeMaker`, `MoneyMachine`).

3. Run the program:
    ```python
    from menu import Menu, MenuItem
    from coffee_maker import CoffeeMaker
    from money_machine import MoneyMachine

    menu = Menu()
    coffee_maker = CoffeeMaker()
    money_machine = MoneyMachine()
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
            if coffee_maker.is_resource_sufficient(drink):
                if money_machine.make_payment(drink.cost):
                    coffee_maker.make_coffee(drink)
    ```

## Usage
- **Turning Off**: To turn off the machine, type `off`.
- **Getting a Report**: To get a report of the current resources and money, type `report`.
- **Selecting a Drink**: Type the name of the drink (e.g., `espresso`, `latte`, `cappuccino`).

## Example Session
```plaintext
What would you like? (espresso/latte/cappuccino): latte
Please insert coins.
how many quarters?: 4
how many dimes?: 0
how many nickels?: 0
how many pennies?: 0
Here is $1.0 in change.
Here is your latte ☕. Enjoy!
What would you like? (espresso/latte/cappuccino): report
Water: 200ml
Milk: 150ml
Coffee: 24g
Money: $2.5
What would you like? (espresso/latte/cappuccino): off
