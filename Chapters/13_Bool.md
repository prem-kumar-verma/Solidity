# Boolean Data Type in Solidity

## 📌 Introduction
The `bool` data type in Solidity represents a boolean value, which can be either `true` or `false`. It is commonly used for conditional logic, state variables, and control structures in smart contracts.

---

## 🔥 1️⃣ **Declaration of Boolean Variables**
Boolean variables are declared using the `bool` keyword.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BooleanExample {
    bool public isActive; // Default value is false

    function activate() public {
        isActive = true;
    }

    function deactivate() public {
        isActive = false;
    }
}
```
🔹 `isActive` is initially `false`. Calling `activate()` sets it to `true`, while `deactivate()` sets it back to `false`.

---

## 🔥 2️⃣ **Boolean Operators in Solidity**
Solidity supports various boolean operators for logical comparisons:
- `!` (NOT) → Reverses the boolean value
- `&&` (AND) → Returns `true` if both operands are `true`
- `||` (OR) → Returns `true` if at least one operand is `true`

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BooleanOperators {
    function checkConditions(bool a, bool b) public pure returns (bool, bool, bool) {
        return (!a, a && b, a || b);
    }
}
```
🔹 This function demonstrates logical NOT, AND, and OR operations.

---

## 🔥 3️⃣ **Boolean Usage in Conditional Statements**
Boolean values are often used in conditional statements to control program flow.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BooleanCondition {
    bool public isEligible;

    function checkEligibility(uint age) public {
        if (age >= 18) {
            isEligible = true;
        } else {
            isEligible = false;
        }
    }
}
```
🔹 `checkEligibility()` sets `isEligible` to `true` if age is 18 or above, otherwise `false`.

---

## 🎯 Summary Table
| Boolean Operator | Description |
|-----------------|-------------|
| `!` (NOT) | Reverses a boolean value |
| `&&` (AND) | Returns `true` if both conditions are `true` |
| `||` (OR) | Returns `true` if at least one condition is `true` |
