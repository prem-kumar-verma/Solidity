# Integer Data Types in Solidity

## 📌 Introduction
In Solidity, integers are fundamental data types used to store numerical values. Solidity supports both **signed** and **unsigned** integers with different bit sizes.

---

## 🔥 Types of Integer Data Types
### 1️⃣ **Signed Integers (`int`)**
- Can hold **both** positive and negative values.
- Available in different sizes from **int8** to **int256** (increments of 8 bits).
- **Alias**: `int` is the same as `int256`.

### 2️⃣ **Unsigned Integers (`uint`)**
- Can hold **only positive** values.
- Available in different sizes from **uint8** to **uint256**.
- **Alias**: `uint` is the same as `uint256`.

#### Example of Different Integer Types:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract IntegerExample {
    int8 public smallNegative = -128;
    int256 public largeNumber = 100000000000;
    uint8 public smallPositive = 255;
    uint256 public largePositive = 100000000000;
}
```

---

## 🚨 Integer Overflow and Underflow
Before Solidity 0.8.0, if an integer exceeded its maximum value, it would **wrap around**, causing overflow or underflow issues. 

### 🔥 Types of Overflow Conditions
1. **Basic Overflow:** When a number exceeds its maximum limit.
2. **Batch Overflow:** When multiple overflow conditions happen in a batch transaction.
3. **Proxy Overflow:** When an attacker manipulates proxy contract storage to cause overflow.

### ⚠️ Example of Overflow (Solidity <0.8.0):
```solidity
pragma solidity ^0.7.0;

contract OverflowExample {
    uint8 public maxUint8 = 255;
    
    function increment() public {
        maxUint8 += 1; // This will cause an overflow and wrap around to 0
    }
}
```

### 🔒 Solidity 0.8.0+ Fix
- **Arithmetic operations now revert on overflow and underflow.**
- SafeMath is no longer required.

```solidity
pragma solidity ^0.8.0;

contract SafeOverflowExample {
    uint8 public maxUint8 = 255;
    
    function increment() public {
        maxUint8 += 1; // This will cause an error instead of overflow
    }
}
```

---

## 🎯 Summary Table
| Integer Type | Range |
|-------------|---------------------------|
| `int8`  | -128 to 127 |
| `int256` (or `int`) | -2¹⁵⁵ to 2¹⁵⁵-1 |
| `uint8` | 0 to 255 |
| `uint256` (or `uint`) | 0 to 2²⁵⁶-1 |

