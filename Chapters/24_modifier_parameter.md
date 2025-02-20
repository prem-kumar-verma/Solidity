# Modifier with Parameter in Solidity

## 📌 Introduction
In Solidity, a `modifier` can also take **parameters** to make it more dynamic and flexible. This allows for additional conditions to be checked before executing a function, improving **security** and **efficiency**.

### ✅ **Key Uses of Modifiers with Parameters**:
1. **Access Control with Dynamic Addresses** – Restrict access to specific users.
2. **Value Restrictions** – Validate input values before execution.
3. **Reusability** – Apply conditions dynamically to different functions.

---

## 🔥 **Example Code: Using `modifier` with Parameter in Solidity**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ModifierWithParameter {
    address public owner;
    uint256 public balance;

    // Modifier with a parameter to check if sender is a specific address
    modifier onlySpecificAddress(address _allowed) {
        require(msg.sender == _allowed, "You are not authorized");
        _; // Continue executing the function
    }

    // Modifier to check if withdrawal is within a limit
    modifier withinLimit(uint256 _amount, uint256 _limit) {
        require(_amount <= _limit, "Amount exceeds limit");
        _; // Continue executing the function
    }

    constructor() {
        owner = msg.sender; // Set the deployer as the owner
    }

    // Function restricted to a specific address using a modifier
    function restrictedAccess(address _allowed) public onlySpecificAddress(_allowed) {
        // Some protected logic
    }

    // Function to withdraw ether with a limit using modifier
    function withdraw(uint256 _amount) public withinLimit(_amount, 5 ether) {
        require(_amount <= balance, "Insufficient funds");
        balance -= _amount;
        payable(msg.sender).transfer(_amount);
    }
}
```

---

## 📌 **Explanation of Code**
1. **`onlySpecificAddress` Modifier**:
   - Takes an address `_allowed` as a parameter.
   - Ensures only that specific address can execute the function.

2. **`withinLimit` Modifier**:
   - Takes `_amount` and `_limit` as parameters.
   - Ensures the withdrawal amount does not exceed the limit.

3. **Restricted Access Function**:
   - Uses `onlySpecificAddress` to control which address can call it.

4. **Withdraw Function**:
   - Uses `withinLimit` to impose a withdrawal cap.
   - Ensures the contract has enough balance before sending Ether.

---

## 🎯 **Key Takeaways**
- **Modifiers with parameters allow dynamic validation**.
- **Improve security** by applying flexible restrictions.
- **Enhance reusability** by making functions more adaptable.
- **Can be used for role-based access and transaction limits**.
