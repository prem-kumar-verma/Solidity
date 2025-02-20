# Require Keyword in Solidity

## 📌 Introduction
The `require` keyword in Solidity is used for input validation and condition enforcement. If the specified condition is not met, the execution of the function stops, and the remaining gas is refunded. This is particularly useful for checking conditions before executing critical code.

### ✅ **Key Uses of `require`**:
1. **Input Validation** – Ensures valid function arguments.
2. **Access Control** – Restricts function access.
3. **State Validation** – Ensures the contract state is correct before proceeding.
4. **Error Handling** – Provides readable error messages.

---

## 🔥 **Example Code: Using `require` in Solidity**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract RequireExample {
    address public owner;
    uint256 public balance;

    constructor() {
        owner = msg.sender; // Setting the deployer as owner
    }

    // Function to deposit ether
    function deposit() public payable {
        require(msg.value > 0, "Deposit must be greater than zero");
        balance += msg.value;
    }

    // Function to withdraw ether
    function withdraw(uint256 _amount) public {
        require(msg.sender == owner, "Only the owner can withdraw");
        require(_amount <= balance, "Insufficient funds");
        balance -= _amount;
        payable(msg.sender).transfer(_amount);
    }
}
```

---

## 📌 **Explanation of Code**
1. **Contract Initialization:**
   - The `owner` variable is set to the deployer's address.
   
2. **Deposit Function:**
   - Users can send Ether to the contract.
   - Uses `require` to check if the deposit amount is greater than zero.
   
3. **Withdraw Function:**
   - Uses `require` to restrict access to only the owner.
   - Checks if the withdrawal amount does not exceed the available balance.
   - If conditions are met, Ether is sent to the owner.

---

## 🎯 **Key Takeaways**
- `require` is essential for **input validation and access control**.
- If `require` fails, the **transaction reverts** and unused gas is refunded.
- It **prevents unwanted state changes** before executing important logic.
- Helps in writing **secure and robust smart contracts**.
