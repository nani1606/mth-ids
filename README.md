# Logical View of the 4+1 Model for a Banking Application


```mermaid
classDiagram
    class BankSystem {
        +AccountController accountController
        +PaymentProcessor paymentProcessor
        +AlertService alertService
        +CustomerManager customerManager
    }

    class AccountController {
        +openAccount()
        +fetchAccount()
        +modifyAccount()
        +closeAccount()
    }

    class PaymentProcessor {
        +startPayment()
        +finalizePayment()
        +reversePayment()
        +viewPaymentHistory()
    }

    class AlertService {
        +sendEmailAlert()
        +sendSmsAlert()
    }

    class CustomerManager {
        +registerCustomer()
        +authenticateCustomer()
        +editCustomerProfile()
        +deleteCustomer()
    }

    class Account {
        +int accountId
        +double accountBalance
        +string accountCategory
        +double checkBalance()
        +void addFunds(double amount)
        +void removeFunds(double amount)
    }

    class Payment {
        +int paymentId
        +int sourceAccount
        +int targetAccount
        +double paymentAmount
        +string paymentStatus
        +void execute()
        +void voidPayment()
    }

    class Customer {
        +int customerId
        +string fullName
        +string contactEmail
        +string hashedPassword
        +bool verifyIdentity()
    }

    BankSystem --> AccountController:holds
    BankSystem --> PaymentProcessor:holds
    BankSystem --> AlertService:holds
    BankSystem --> CustomerManager:holds

    AccountController --> Account:controls
    PaymentProcessor --> Payment:process
    CustomerManager --> Customer:manages
    AlertService --> Customer:alerts
