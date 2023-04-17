MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}
hidden_account_balance = 0
profit = 0
resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}
def reports():
    print(f"Water: {resources['water']}ml")
    print(f"Milk: {resources['milk']}ml")
    print(f"Coffee: {resources['coffee']}g")
    print(f"Money: ${profit}")

def is_enough_resources(order_ingredients):
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"sorry there is not enough {item}")
            return False
    return True

def process_coins(drink_cost):
    print(f"Please pay for your drink. The cost is ${drink_cost}.")
    print("Accepted bills: $1, $5, $10, $20")
    total = 0
    refund = False
    while total < drink_cost:
        try:
            total += int(input("Enter the value of the bill you want to insert ($1, $5, $10, $20): "))
            if total >= drink_cost:
                break
        except ValueError:
            print("Invalid input, please enter a number.")
            continue

        print(f"Amount paid so far: ${total}. The drink cost ${drink_cost}.")
        retry = input("Do you want to insert more bills, get a refund, or cancel the order? (insert/refund/cancel): ")
        if retry == "refund" or retry == "cancel":
            refund = True
            break
    if refund:
        print(f"Here is your ${total} refund.")
        return 0
    else:
        return total

import random

def calculate_change(payment, drink_cost):
    remaining_change = round((payment - drink_cost) * 100)  # Convert to cents

    quarters = dimes = nickles = pennies = 0

    while remaining_change > 0:
        coin_type = random.choice(["quarters", "dimes", "nickles", "pennies"])

        if coin_type == "quarters" and remaining_change >= 25:
            quarters += 1
            remaining_change -= 25
        elif coin_type == "dimes" and remaining_change >= 10:
            dimes += 1
            remaining_change -= 10
        elif coin_type == "nickles" and remaining_change >= 5:
            nickles += 1
            remaining_change -= 5
        elif coin_type == "pennies" and remaining_change >= 1:
            pennies += 1
            remaining_change -= 1

    return f"Your change is: {quarters} quarters, {dimes} dimes, {nickles} nickles, and {pennies} pennies."

def ask_for_tip(payment, drink_cost):
    while True:
        tip_decision = input("Do you want to give a tip? yes/no: ").lower()
        if tip_decision == "yes":
            full_tip = input("Do you want to give the remaining amount as a tip? yes/no: ").lower()
            if full_tip == "yes":
                tip = payment - drink_cost
                print(f"Thank you for the ${tip} tip!")
                break
            else:
                try:
                    tip = float(input("How much do you want to give as a tip?: "))
                    if 0 <= tip <= (payment - drink_cost):
                        print(f"Thank you for the ${tip} tip!")
                        break
                    else:
                        print("Invalid tip amount.")
                except ValueError:
                    print("Invalid input, please enter a number.")
        elif tip_decision == "no":
            break
        else:
            print("Invalid input, please enter 'yes' or 'no'.")



def ask_yes_no_question(prompt):
    while True:
        answer = input(prompt).lower()
        if answer == 'yes' or answer == 'no':
            return answer
        else:
            print("Invalid input. Please enter 'yes' or 'no'.")


def the_trans_good(user_money, drink_cost):
    if user_money >= drink_cost:
        change = round(user_money - drink_cost, 2)
        tip = 0
        if user_money > drink_cost:
            print(f"The remaining amount is ${change}.")
            print("Do you want to give a tip?")

            while True:
                give_tip = input("yes/no: ").lower()
                if give_tip == 'yes':
                    print("Do you want to give the remaining amount as a tip?")

                    while True:
                        give_full_change_as_tip = input("yes/no: ").lower()
                        if give_full_change_as_tip == 'yes':
                            tip = change
                            break
                        elif give_full_change_as_tip == 'no':
                            max_tip = round(change, 2)
                            print(f"The remaining amount is ${max_tip}. How much do want to give as a tip?")

                            while True:
                                try:
                                    tip = float(input())
                                    if tip <= max_tip:
                                        break
                                    else:
                                        print(f"Please enter an amount less than or equal to ${max_tip} ")
                                except ValueError:
                                    print("Please enter a valid number.")
                            break
                        else:
                            print("Invalid input. Please enter 'yes' or 'no'.")
                    break
                elif give_tip == 'no':
                    break
                else:
                    print("Invalid input. Please enter 'yes' or 'no'.")

            change -= tip

        if change != 0:
            print(f"Here is ${change} in change")
        global profit
        profit += drink_cost
        profit += tip
        return True
    else:
        print("Sorry, not enough money.")
        return False


def make_coffe(drink_name, order_ingredient):
    for item in order_ingredient:
        resources[item] -= order_ingredient[item]
    print(f"Here is your {drink_name}")

def add_resources():
    resources['water'] += int(input("how much water do you want to add?"))
    resources['milk'] += int(input("how much milk do you want to add?"))
    resources['coffee'] += int(input("how much coffe do you want to add?"))
    print("Resources added successfully!")

hidden_account = 0

def transfer_to_hidden_account(amount, password):
    global hidden_account_balance
    global profit
    if password == "crash" and amount <= profit:
        hidden_account_balance += amount
        profit -= amount
        print(f"${amount} has been transferred to the hidden account.")
    else:
        print("Incorrect password or insufficient funds.")
def view_hidden_account_balance(password):
    global hidden_account_balance
    if password == "crash":
        print(f"Hidden Account Balance: ${hidden_account_balance}")
    else:
        print("Invalid password. Access denied.")

def transfer_from_hidden_account(amount, password):
    global profit, hidden_account_balance
    if password == "crash":
        if hidden_account_balance >= amount:
            hidden_account_balance -= amount
            profit += amount
            print(f"${amount} has been transferred from the hidden account to the main account.")
        else:
            print("Not enough balance in the hidden account to transfer the requested amount.")
    else:
        print("Invalid password. Transfer failed.")
def input_valid_currency(prompt):
    while True:
        try:
            value = int(input(prompt))
            return value
        except ValueError:
            print("Invalid input. Please enter a number.")

def display_profit():
    print(f"Profit: ${profit}")


is_on = True
password = None
correct_password_attempts = 0

while is_on:
    choice = ""
    password_attempts = 3

    while choice not in MENU and choice not in ["off", "report", "add", "refund", "transfer_to", "transfer_from",
                                                "view_hidden_balance", "hidden", "profit"]:
        choice = input("What would you like to order? (espresso/latte/cappuccino):").lower()

    if choice == "off":
        is_on = False
    elif choice == "profit":
        display_profit()

    elif choice == "report":
        reports()

    elif choice == "add":
        add_resources()

    elif choice == "refund":
        print("Refund is only available during payment process")
    elif choice == "hidden":
        if password_attempts > 0 and correct_password_attempts > 0:
            password_attempts = 3
            correct_password_attempts = 0
        password = input("Enter the password to access the hidden account: ")
        if password == "crash":
            correct_password_attempts += 1
            choice = input("What would you like to do? (transfer_to/transfer_from/view_hidden_balance): ").lower()
            if choice == "transfer_to":
                amount = float(input("Enter the amount to transfer to the hidden account: "))
                transfer_to_hidden_account(amount, password)
            elif choice == "transfer_from":
                amount = float(input("Enter the amount to transfer from the hidden account: "))
                transfer_from_hidden_account(amount, password)
            elif choice == "view_hidden_balance":
                view_hidden_account_balance(password)
        else:
            print(f"Invalid password. {password_attempts - 1} attempts remaining.")
            password_attempts -= 1
            if password_attempts <= 0:
                print("Access to the hidden account has been denied.")
    else:
        drink = MENU[choice]
        if is_enough_resources(drink["ingredients"]):
            payment = process_coins(drink["cost"])
            if payment != 0:
                if the_trans_good(payment, drink["cost"]):
                    make_coffe(choice, drink["ingredients"])
                    change_message = calculate_change(payment, drink["cost"])
                    print(change_message)
                else:
                    print(f"Here is your ${payment} refund.")
