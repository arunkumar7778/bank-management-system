from abc import ABC, abstractmethod


class InvalidOperationError(Exception):
    pass


class Bank(ABC):

    @abstractmethod
    def add(self, account_no, account_types, name, age, phone_no, balance) -> None:
        pass

    @abstractmethod
    def __getitem__(self, item):
        pass

    @abstractmethod
    def __len__(self):
        pass

    @abstractmethod
    def __iter__(self):
        pass

    @abstractmethod
    def deposit_amount(self, account_no):
        pass

    @abstractmethod
    def withdraw_amount(self, account_no):
        pass


class SavingsAccount(Bank):

    def __init__(self, account_no=2002141, account_types='S', name='vinothan nc', age=20, phone_no=8778786481,
                 balance=5000.0):
        self.__customer = {account_no: {'account_type': account_types, 'name': name, 'age': age, 'phone_nno': phone_no,
                                        'balance': balance}}

    def add(self, account_no, account_types, name, age, phone_no, balance) -> None:
        self.__customer[account_no] = {'account_type': account_types, 'name': name, 'age': age, 'phone_no': phone_no,
                                       'balance': balance}

    def __getitem__(self, account_no):
        return self.__customer.get(account_no, "Not Found")

    def __len__(self):
        return len(self.__customer)

    def __iter__(self):
        return iter(self.__customer.items())

    def deposit_amount(self, account_no) -> None:
        if account_no in self.__customer:
            user_amount: float = float(input("> Enter amount to deposit : "))
            if user_amount < 0:
                print("Enter proper amount to deposit")
            current_balance = self.__customer[account_no].get("balance", 0)
            new_balance = current_balance + user_amount
            self.__customer[account_no]["balance"] = new_balance
            print(f"₹{user_amount} is deposited in to Savings Account")
            print(f"Balance : {new_balance}")
        else:
            print("Invalid (Account Number)")

    def withdraw_amount(self, account_no):
        if account_no in self.__customer:
            user_amount: float = float(input("> Enter Amount to withdraw : "))
            if user_amount > 0:
                if user_amount < self.__customer[account_no].get('balance'):
                    current_balance = self.__customer[account_no].get('balance', 0)
                    new_balance = current_balance - user_amount
                    self.__customer[account_no]["balance"] = new_balance
                    print(f"{user_amount} is withdraw from Savings Account")
                    print(f"Balance : {new_balance}")

                else:
                    print("Invalid value (Amount)")
            else:
                print("Invalid value (Amount)")
        else:
            print("Invalid (Account Number)")


class CredictCard(Bank):

    def __init__(self, account_no=71382002141, account_types='C', name='vinothan nc', age=20, phone_no=8778786481,
                 balance=10000.0):
        self.__customer = {account_no: {'account_type': account_types, 'name': name, 'age': age, 'phone_no': phone_no,
                                        'balance': balance}}

    def add(self, account_no, account_types, name, age, phone_no, balance) -> None:
        self.__customer[account_no] = {'account_type': account_types, 'name': name, 'age': age, 'phone_no': phone_no,
                                       'balance': balance}

    def __getitem__(self, account_no):
        return self.__customer.get(account_no, 'Not Found')

    def __len__(self):
        return len(self.__customer)

    def __iter__(self):
        return iter(self.__customer.items())

    def deposit_amount(self, account_no: int):
        if account_no in self.__customer:

            user_amount: float = float(input("> Enter amount to deposit : "))
            if user_amount < 0:
                print("Enter proper amount to deposit")
            current_balance = self.__customer[account_no].get("balance")
            new_balance = current_balance + user_amount
            self.__customer[account_no]["balance"] = new_balance
            print(f"₹{user_amount} is deposit in the Credit Card Account")
            print(f"Balance : ₹{new_balance}")

        else:
            print("Invalid (Account Number)")

    def withdraw_amount(self, account_no: int):
        if account_no in self.__customer:
            user_amount: float = float(input("> Enter amount to withdraw : "))
            if user_amount > 0:
                if user_amount < self.__customer[account_no].get('balance'):
                    current_balance = self.__customer[account_no].get('balance', 0)
                    new_balance = current_balance - user_amount
                    self.__customer[account_no]['balance'] = new_balance
                    print(f"₹{user_amount} is withdraw from Credit Card Account")
                    print(f"Balance : ₹{new_balance}")

            else:
                print("Invalid value (Amount)")
        else:
            print("Invalid (Account Number)")


def savings() -> None:
    saving_account = SavingsAccount()
    try:
        user_transaction = input("Deposit (D) | Withdraw (W) : ").upper().strip()

        if user_transaction == "D":
            user_account_no: int = int(input("> Account Number : "))
            saving_account.deposit_amount(user_account_no)

        elif user_transaction == "W":
            user_account_no: int = int(input("> Account Number : "))
            saving_account.withdraw_amount(user_account_no)

        else:
            print("Invalid Input (Transaction).")

    except ValueError:
        print("Invalid Input (Account Number).")


def credit():
    credit_account = CredictCard()
    try:
        user_transaction = input("Deposit (D) | Withdraw (W) : ").upper().strip()
        if user_transaction == "D":
            user_account_no: int = int(input("> Account Number : "))
            credit_account.deposit_amount(user_account_no)

        elif user_transaction == "W":
            user_account_no: int = int(input("> Account Number : "))
            credit_account.withdraw_amount(user_account_no)

        else:
            print("Invalid Input (Transaction).")

    except ValueError:
        print("Invalid Input (Account Number).")


def amount():
    print("Note : 'Minimum Balance' should be maintained (₹ 1000 )")
    user_amount: float = float(input("> Amount to deposit in Account ₹ : "))
    if user_amount < 1000:
        print("--- Amount should be at least ₹1000 ---")
        return user_amount
    else:
        print()
        print("'AMOUNT DEPOSITED SUCCESSFULLY'")
        print()
        return user_amount


def new_account_type() -> None:
    try:
        print_lines()
        user_phone: int = int(input("Phone No : "))
        user_account_type: str = input("Savings account (S) | Credit Card Account (C) : ").upper().strip()
        print("Account number has sent in via message")

        if user_account_type == "S":

            greetings("SAVINGS ACCOUNT")
            saving_user_account_no: int = int(input("> Savings Account Number : "))
            savings_account = SavingsAccount()
            saving_user_name: str = input("> Your Name : ").lower().strip()
            saving_user_age: int = int(input("> Your Age : "))
            saving_user_amount = amount()
            if saving_user_amount > 1000:
                savings_account.add(account_no=saving_user_account_no, account_types=user_account_type,
                                    name=saving_user_name,
                                    age=saving_user_age, phone_no=user_phone, balance=saving_user_amount)

                greetings("ACCOUNT CREATED SUCCESSFULLY")

                account_info = savings_account.__getitem__(saving_user_account_no)
                if account_info != "Not Found":
                    print(f"Savings Account Number: {saving_user_account_no}")
                    for key, value in account_info.items():
                        print(f"{key}: {value}")
                else:
                    print("Account not found!")

            print_lines()

        elif user_account_type == "C":

            greetings("CREDIT CARD ACCOUNT")
            credit_account_no: int = int(input("> Credit Card Account Number : "))
            credit_card = CredictCard()
            credit_user_name: str = input("> Your Name : ").lower().strip()
            credit_user_age: int = int(input("> Your Age : "))
            credit_user_amount = amount()
            if credit_user_amount > 1000:
                credit_card.add(account_no=credit_account_no, account_types=user_account_type, name=credit_user_name,
                                age=credit_user_age, phone_no=user_phone, balance=credit_user_amount)
                greetings("ACCOUNT CREATED SUCCESSFULLY")

                account_info = credit_card.__getitem__(credit_account_no)
                if account_info != 'No Found':
                    print(f"Credit Card Number : {credit_account_no}")
                    for key, value in account_info.items():
                        print(f"{key} : {value}")
                print_lines()

        else:
            print("There are two account types to choose from.")

    except (InvalidOperationError, ValueError):
        print("Provide proper value for required fields")


def account_type() -> None:
    user_input = input("> Savings Account (S) | Credit card (C) : ").upper().strip()
    if user_input == "S":
        savings()
    elif user_input == "C":
        credit()
    else:
        print("Wrong Account Type!")


def main() -> None:
    user_response = 'yes'
    greetings("WELCOME NCV BANK")
    while True:
        if user_response == 'yes':
            account_exists = input("Do you have Account Yes | No : ").lower().strip()
            if account_exists.isdigit():
                raise InvalidOperationError

            if account_exists == "yes":
                account_type()
            elif account_exists == "no":
                new_account_type()
            else:
                print("Invalid Operation!")

        elif user_response == "no":
            greetings("THANK YOU NCV BANK")
            quit()

        else:
            print("Invalid Operation!")

        user_response = input("Continue Yes | NO : ").lower().strip()


def greetings(value) -> None:
    print('-' * 10, value, '-' * 10)


def print_lines() -> None:
    print("-" * 30)


if __name__ == '__main__':
    main()
