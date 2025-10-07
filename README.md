# 🏦 ATM Machine Use Case Diagram — README

## 📘 **Overview**

This document provides a detailed explanation of the **ATM Machine Use Case Diagram**.
The diagram models the interactions between users (actors) and the ATM system, describing how customers, bank staff, and external systems work together to perform essential banking operations such as cash withdrawal, deposits, balance inquiries, and fund transfers.

---

## 🎯 **Purpose**

The goal of the ATM system is to:

* Allow **customers** to perform secure financial transactions.
* Enable **bank administrators** to monitor and report ATM activities.
* Provide **technicians** with maintenance and cash refilling capabilities.
* Ensure the **bank system** authorizes and updates account balances in real-time.

---

## 👥 **Actors**

| Actor           | Description                                                                    |
| --------------- | ------------------------------------------------------------------------------ |
| **Customer**    | Primary user who interacts with the ATM to perform banking transactions.       |
| **Bank System** | External system that authorizes, validates, and updates customer transactions. |
| **Technician**  | Responsible for maintaining the ATM machine and refilling cash.                |
| **Bank Admin**  | Monitors ATM operations, generates reports, and ensures proper functioning.    |

---

## ⚙️ **Main Use Cases**

### 1. **Enter Card**

The customer inserts a valid ATM card to begin a session.

### 2. **Enter PIN**

The system prompts the user to input their Personal Identification Number for authentication.

### 3. **Authentication**

The ATM verifies the entered PIN and card details with the bank system.

* If valid → access granted
* If invalid → transaction terminated

### 4. **Perform Transaction**

The central use case that allows customers to execute different types of banking operations.
This use case **includes** authentication and connects to several sub-use cases.

#### Includes:

* **Withdraw Cash**
* **Deposit Funds**
* **Transfer Funds**
* **Check Balance**

#### Extends:

* **Print Receipt** (optional)

### 5. **Withdraw Cash**

The customer withdraws money from their account. The system checks balance and requests authorization from the bank system before dispensing cash.

### 6. **Deposit Funds**

Allows the customer to deposit money into their account. The ATM verifies the deposit and updates the account via the bank system.

### 7. **Transfer Funds**

Transfers money between two customer accounts. Requires authorization from the bank system.

### 8. **Check Balance**

Displays the account balance to the customer.

### 9. **Print Receipt**

Provides a printed record of the completed transaction (optional extension).

---

## 🖥️ **Supporting Use Cases**

### **Authorize Transaction**

Triggered automatically when a financial transaction is requested. The bank system validates and authorizes the transaction.

### **Update Balance**

Updates the customer’s account after a successful transaction.

---

## 🧰 **Maintenance and Administration Use Cases**

| Actor          | Use Case                 | Description                                                              |
| -------------- | ------------------------ | ------------------------------------------------------------------------ |
| **Technician** | **Maintain ATM Machine** | Handles technical and physical maintenance.                              |
| **Technician** | **Refill Cash**          | Refills the cash storage to keep the ATM operational.                    |
| **Bank Admin** | **Monitor Transactions** | Monitors ongoing ATM operations and activities.                          |
| **Bank Admin** | **Generate Reports**     | Produces periodic reports of ATM usage, transactions, and system health. |

---

## 🔄 **Relationships**

| Relationship Type         | Example                                | Description                                                           |
| ------------------------- | -------------------------------------- | --------------------------------------------------------------------- |
| **Include (<<include>>)** | `Perform Transaction → Authentication` | Indicates that authentication is a required step in all transactions. |
| **Extend (<<extend>>)**   | `Withdraw Cash → Print Receipt`        | Represents optional functionality (printing a receipt).               |
| **Association**           | `Customer — Perform Transaction`       | Shows interaction between an actor and a use case.                    |

---

## ⚠️ **Identified Issues in Original Diagram**

1. “Valid” shown as a use case (should be a condition).
2. Wrong direction of `<<include>>` between “Transfer Funds” and “Perform Transaction.”
3. Missing `<<extend>>` for “Print Receipt.”
4. “Technician” and “Bank Admin” placed inside the system boundary.
5. “Bank System” misuse — should be external, not performing use cases directly.
6. Inconsistent naming and coloring.

---

## ✅ **Corrected Design Suggestions**

* Make **“Perform Transaction”** the parent use case for all transaction types.
* Add **include/extend** relationships correctly.
* Keep all **actors outside** the system boundary.
* Treat **Bank System** as an **external entity**.
* Remove the “Valid” use case and represent it as a condition.

---

## 📄 **Conclusion**

This use case diagram models the **functional behavior** of an ATM Machine System, focusing on secure customer transactions, backend validation, and administrative control.
It ensures clarity in responsibilities, improves system understanding, and forms the foundation for further system design and implementation.
