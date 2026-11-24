# CIMB Digital Bank - Decorator Pattern

## Problem Statement

CIMB is a digital bank that offers GSave and UpSave savings accounts. As with a typical Savings Account, it contains accountNumber, accountName, and a balance for that account.

The typical savings account offers an interest rate of 1%.
The benefits of the typical savings account is the same with the "Standard Savings Account" as compared to other banks.

The GSave account offers an interest rate of 2.5%.
Benefits include the "Standard Savings Account" plus access to "GCash transfer".

The UpSave account offers the highest interest rate of 4.0%.
Benefits include the "Standard Savings Account" plus "with Insurance".

Develop a decorator pattern approach that will implement the given UML diagram:

## UML Class Diagram

```mermaid
classDiagram
    class BankAccount {
        <<interface>>
        +showAccountType() String
        +getInterestRate() Double
        +getBalance() Double
        +showBenefits() String
        +computeBalanceWithInterest() Double
        +showInfo() String
    }

    class BankAccountDecorator {
        <<interface>>
        +setBankAccount(bankAccount: BankAccount) void
    }

    class SavingsAccount {
        -accountNumber: int
        -accountName: String
        -balance: Double
        +getAccountNumber() int
        +setAccountNumber(accountNumber: int) void
        +getAccountName() String
        +setAccountName(accountName: String) void
        +getBalance() Double
        +setBalance(balance: Double) void
        +showAccountType() String
        +getInterestRate() Double
        +showBenefits() String
        +computeBalanceWithInterest() Double
        +showInfo() String
    }

    class GSave {
        -bankAccount: BankAccount
        +GSave(bankAccount: BankAccount)
        +setBankAccount(bankAccount: BankAccount) void
        +showAccountType() String
        +getInterestRate() Double
        +getBalance() Double
        +showBenefits() String
        +computeBalanceWithInterest() Double
        +showInfo() String
    }

    class UpSave {
        -bankAccount: BankAccount
        +UpSave(bankAccount: BankAccount)
        +setBankAccount(bankAccount: BankAccount) void
        +showAccountType() String
        +getInterestRate() Double
        +getBalance() Double
        +showBenefits() String
        +computeBalanceWithInterest() Double
        +showInfo() String
    }

    class Cimb {
        +main(args: String[]) void
    }

    BankAccount <|.. SavingsAccount : implements
    BankAccount <|-- BankAccountDecorator : extends
    BankAccountDecorator *-- BankAccount : wraps
    BankAccountDecorator <|.. GSave : implements
    BankAccountDecorator <|.. UpSave : implements
    Cimb --> BankAccount : uses
```
