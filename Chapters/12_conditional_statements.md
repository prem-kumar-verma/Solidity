# Conditional Statements in Solidity

## 📌 Introduction
Conditional statements in Solidity allow execution of different code blocks based on specific conditions. Solidity supports:
- **If statements**
- **If-else statements**
- **Else-if ladder**
- **Ternary operator**

---

## 🔥 1️⃣ **If Statement**
- Executes a block of code if the condition evaluates to `true`.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract IfExample {
    uint public number;

    function setNumber(uint _num) public {
        if (_num > 0) {
            number = _num;
        }
    }
}
```
🔹 If `_num > 0`, it updates `number`, otherwise, nothing happens.

---

## 🔥 2️⃣ **If-Else Statement**
- If the condition is `true`, the first block executes; otherwise, the second block executes.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract IfElseExample {
    string public result;

    function checkNumber(int _num) public {
        if (_num > 0) {
            result = "Positive";
        } else {
            result = "Negative or Zero";
        }
    }
}
```
🔹 The contract stores "Positive" if `_num > 0`, otherwise "Negative or Zero".

---

## 🔥 3️⃣ **Else-If Ladder**
- Used when multiple conditions need to be checked sequentially.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ElseIfExample {
    string public category;

    function categorizeAge(uint _age) public {
        if (_age < 13) {
            category = "Child";
        } else if (_age >= 13 && _age < 18) {
            category = "Teenager";
        } else {
            category = "Adult";
        }
    }
}
```
🔹 The contract categorizes based on age.

---

## 🔥 4️⃣ **Ternary Operator**
- A shorthand for `if-else` statements.
- Syntax: `condition ? value_if_true : value_if_false;`

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract TernaryExample {
    string public status;

    function checkEvenOdd(uint _num) public {
        status = (_num % 2 == 0) ? "Even" : "Odd";
    }
}
```
🔹 The contract assigns "Even" if `_num` is even, otherwise "Odd".

---

## 🎯 Summary Table
| Conditional Type | Usage |
|-----------------|--------|
| **If Statement** | Executes code if condition is `true` |
| **If-Else** | Executes one block if `true`, another if `false` |
| **Else-If Ladder** | Checks multiple conditions sequentially |
| **Ternary Operator** | Short-hand `if-else` for compact conditions |
