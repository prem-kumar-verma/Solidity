# Functions of Solidity (Getters and Setters)

## 📌 Introduction
Solidity functions are categorized into **getters** and **setters**.
- **Getter functions** allow users to retrieve stored values from a smart contract **without modifying** the blockchain.
- **Setter functions** modify the contract state, triggering a **transaction that requires gas fees**.

## 🔥 Key Concepts
1. **Calling a setter function creates a transaction** that needs to be mined and costs gas.
2. **Calling a getter function is free** since it does not alter the blockchain state.
3. **Public state variables automatically generate a getter function**.
4. **By default, variables in Solidity are private**, meaning they cannot be accessed externally unless specified otherwise.

---

## 📜 Solidity Code Example
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Example {
    uint private number;  // Private state variable

    // Setter function: modifies state, requires gas
    function setNumber(uint _num) public {
        number = _num;
    }

    // Getter function: retrieves value, does not cost gas
    function getNumber() public view returns (uint) {
        return number;
    }
}
```

### 🛠 Explanation:
- **`setNumber(uint _num)`** is a setter function that **modifies** the state variable `number`. Since it changes the blockchain, it incurs a **gas cost**.
- **`getNumber()`** is a getter function that retrieves the stored value of `number` **without modifying** the state.

---

## 🔗 Auto-Generated Getter for Public Variables
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract AutoGetter {
    uint public myNumber; // Automatically generates a getter function
}
```
- Since `myNumber` is **public**, Solidity **automatically** generates a getter function.
- We can call `myNumber()` externally without defining a separate `getMyNumber()` function.

---

## 🎯 Summary
| Function Type | Requires Gas? | Changes State? | Automatically Created? |
|--------------|--------------|----------------|----------------------|
| Getter | ❌ No | ❌ No | ✅ Yes (if variable is public) |
| Setter | ✅ Yes | ✅ Yes | ❌ No |

- Use **getter functions** to retrieve data without gas costs.
- Use **setter functions** when you need to modify blockchain data (requires gas fees).
- Declaring a **public** state variable automatically creates a getter.
- **Default visibility is private**, so explicitly declare variables public if needed.

🚀 **Happy Coding with Solidity!**
