def filipino_denomination_breakdown(amount):
    denominations = [1000, 500, 200, 100, 50, 20, 10, 5, 1]
    breakdown = {}
    for denomination in denominations:
        count = amount // denomination
        if count > 0:
            breakdown[denomination] = count
            amount -= count * denomination
    return breakdown

def bank_simulation():
    accounts = {}
    while True:
        print("\nBank Simulation Menu:")
        print("1. Create New Account")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Check Balance")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            name = input("Enter account name: ")
            initial_deposit = float(input("Enter initial deposit: "))
            accounts[name] = initial_deposit
            print("Account created successfully!")

        elif choice == '2':
            name = input("Enter account name: ")
            if name in accounts:
                deposit_amount = float(input("Enter deposit amount: "))
                accounts[name] += deposit_amount
                print("Deposit successful!")
                print("Current balance:", accounts[name])
                breakdown = filipino_denomination_breakdown(int(accounts[name]))
                print("Denomination Breakdown:", breakdown)

            else:
                print("Account does not exist.")

        elif choice == '3':
            name = input("Enter account name: ")
            if name in accounts:
                withdraw_amount = float(input("Enter withdraw amount: "))
                if accounts[name] >= withdraw_amount:
                    accounts[name] -= withdraw_amount
                    print("Withdrawal successful!")
                    print("Current balance:", accounts[name])
                    breakdown = filipino_denomination_breakdown(int(accounts[name]))
                    print("Denomination Breakdown:", breakdown)
                else:
                    print("Insufficient balance.")
            else:
                print("Account does not exist.")

        elif choice == '4':
            name = input("Enter account name: ")
            if name in accounts:
                print("Current balance:", accounts[name])
                breakdown = filipino_denomination_breakdown(int(accounts[name]))
                print("Denomination Breakdown:", breakdown)
            else:
                print("Account does not exist.")

        elif choice == '5':
            print("Exiting program...")
            break

        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    bank_simulation()
