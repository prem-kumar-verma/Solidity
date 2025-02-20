# Modifier Keyword in Solidity

## 📌 Introduction
In Solidity, a `modifier` is a special function used to **change the behavior of a function** without modifying its code. Modifiers help in **reusability**, **access control**, and **input validation**.

### ✅ **Key Uses of Modifiers**:
1. **Access Control** – Restrict certain functions to specific users.
2. **Input Validation** – Ensure conditions before executing a function.
3. **Reusability** – Reduce code duplication.

---

## 🔥 **Example Code: Using `modifier` in Solidity**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ModifierExample {
    address public owner;
    uint256 public balance;

    // Modifier to restrict access to only the owner
    modifier onlyOwner() {
        require(msg.sender == owner, "You are not the owner");
        _; // Continue executing the function
    }

    // Modifier to ensure non-zero deposits
    modifier validDeposit(uint256 _amount) {
        require(_amount > 0, "Deposit must be greater than zero");
        _; // Continue executing the function
    }

    constructor() {
        owner = msg.sender; // Set the deployer as the owner
    }

    // Function to deposit ether using modifier
    function deposit() public payable validDeposit(msg.value) {
        balance += msg.value;
    }

    // Function to withdraw ether using onlyOwner modifier
    function withdraw(uint256 _amount) public onlyOwner {
        require(_amount <= balance, "Insufficient funds");
        balance -= _amount;
        payable(msg.sender).transfer(_amount);
    }
}
```

---

## 📌 **Explanation of Code**
1. **`onlyOwner` Modifier**:
   - Ensures only the owner can call specific functions.
   - Uses `require` to check if `msg.sender` is the owner.
   - `_` means the rest of the function executes after validation.

2. **`validDeposit` Modifier**:
   - Ensures the deposit amount is greater than zero.
   - If the condition is met, the function executes.

3. **Deposit and Withdraw Functions**:
   - The `deposit` function uses `validDeposit` to check the amount.
   - The `withdraw` function uses `onlyOwner` to restrict access.

---

## 🎯 **Key Takeaways**
- **Modifiers improve security and readability**.
- **Prevent unnecessary execution** if conditions are not met.
- **Code reusability** reduces redundant logic.
- **Enhances access control** by restricting unauthorized actions.
