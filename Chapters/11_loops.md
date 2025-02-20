# Loops in Solidity

## 📌 Introduction
Loops in Solidity are used to execute a block of code multiple times until a specified condition is met. Solidity supports **for**, **while**, and **do-while** loops, similar to other programming languages.

---

## 🔥 Key Points About Loops in Solidity
- Loops must be declared **inside functions**.
- Solidity is a gas-constrained environment, so **avoid infinite loops**.
- Keep loops optimized to prevent excessive gas consumption.

---

## 🔄 1️⃣ **For Loop**
- Used when the number of iterations is known beforehand.
- Executes the block of code a fixed number of times.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ForLoopExample {
    uint[] public numbers;

    function addNumbers() public {
        for (uint i = 1; i <= 5; i++) {
            numbers.push(i);
        }
    }
}
```

---

## 🔄 2️⃣ **While Loop**
- Used when the number of iterations is unknown but depends on a condition.
- The loop runs until the condition is **false**.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract WhileLoopExample {
    uint public count;

    function incrementWhile() public {
        while (count < 5) {
            count++;
        }
    }
}
```

---

## 🔄 3️⃣ **Do-While Loop**
- Similar to **while loop**, but ensures that the loop body runs **at least once** before checking the condition.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DoWhileLoopExample {
    uint public count;

    function incrementDoWhile() public {
        do {
            count++;
        } while (count < 5);
    }
}
```

---

## 🎯 Summary Table
| Loop Type | Condition Check | Use Case |
|-----------|----------------|------------|
| **For Loop** | Before iteration | When the number of iterations is known |
| **While Loop** | Before iteration | When the number of iterations is unknown |
| **Do-While Loop** | After iteration | When execution must occur at least once |

