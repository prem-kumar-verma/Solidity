# Enums in Solidity

## 📌 Introduction
Enums in Solidity provide a way to define a user-defined type with a set of named values. They are useful for representing finite states in a readable and structured way.

---

## 🔥 1️⃣ **Declaring an Enum**
Enums are defined using the `enum` keyword followed by a name and a set of possible values.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract EnumExample {
    // Define an Enum
    enum Status { Pending, Approved, Rejected }
}
```
🔹 This defines an `enum` named `Status` with three possible values: `Pending`, `Approved`, and `Rejected`.

---

## 🔥 2️⃣ **Using Enums in Solidity**
Enums can be used as state variables to store values and manage contract logic.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract EnumExample {
    enum Status { Pending, Approved, Rejected }
    
    // Declare a state variable
    Status public applicationStatus;

    // Set default value (automatically set to the first enum value, i.e., Pending)
    constructor() {
        applicationStatus = Status.Pending;
    }

    // Function to set status
    function setStatus(Status _status) public {
        applicationStatus = _status;
    }

    // Function to get status
    function getStatus() public view returns (Status) {
        return applicationStatus;
    }
}
```
🔹 `applicationStatus` holds the enum value. The `setStatus()` function updates the status, and `getStatus()` retrieves it.

---

## 🔥 3️⃣ **Enum with Conditional Logic**
Enums help implement conditional logic based on the contract state.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract OrderProcess {
    enum OrderStatus { Placed, Shipped, Delivered, Cancelled }

    OrderStatus public currentStatus;

    function placeOrder() public {
        currentStatus = OrderStatus.Placed;
    }

    function shipOrder() public {
        require(currentStatus == OrderStatus.Placed, "Order must be placed first");
        currentStatus = OrderStatus.Shipped;
    }

    function deliverOrder() public {
        require(currentStatus == OrderStatus.Shipped, "Order must be shipped first");
        currentStatus = OrderStatus.Delivered;
    }
}
```
🔹 This contract manages an order lifecycle using an enum.

---

## 🎯 Summary Table
| Feature | Description |
|-----------------|-------------|
| `enum` | Defines a user-defined type with named values |
| Default Value | The first declared value is assigned as the default |
| State Variable | Stores an enum value within a contract |
| Function Control | Enums can control logic flow efficiently |

