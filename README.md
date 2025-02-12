#include <iostream>
#include <string>

class BankAccount {
private:
    int accountNumber;
    double balance;
    std::string accountHolderName;

public:
    BankAccount(int accNum, std::string accName, double initialBalance)
        : accountNumber(accNum), accountHolderName(accName), balance(initialBalance) {}

    void deposit(double amount) { 
        if (amount > 0) balance += amount; 
        std::cout << "Deposited: $" << amount << "\n"; 
    }

    void withdraw(double amount) { 
        if (amount > 0 && amount <= balance) balance -= amount; 
        else std::cout << "Insufficient funds or invalid amount!\n"; 
    }

    void displayBalance() { std::cout << "Current Balance: $" << balance << "\n"; }
};

int main() {
    int accNum;
    std::string accName;
    double initialBalance;

    std::cout << "Enter Account Number: "; std::cin >> accNum;
    std::cin.ignore();  
    std::cout << "Enter Account Holder Name: "; std::getline(std::cin, accName);
    std::cout << "Enter Initial Balance: "; std::cin >> initialBalance;

    BankAccount myAccount(accNum, accName, initialBalance);

    int choice;
    do {
        std::cout << "\n1. Deposit  2. Withdraw  3. Display Balance  4. Exit\nChoose: ";
        std::cin >> choice;
        if (choice == 1) { double amt; std::cout << "Deposit: "; std::cin >> amt; myAccount.deposit(amt); }
        else if (choice == 2) { double amt; std::cout << "Withdraw: "; std::cin >> amt; myAccount.withdraw(amt); }
        else if (choice == 3) myAccount.displayBalance();
    } while (choice != 4);

    return 0;
}
