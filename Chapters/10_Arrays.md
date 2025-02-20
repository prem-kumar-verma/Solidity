# Arrays in Solidity

## 📌 Introduction
In Solidity, arrays are used to store multiple values of the same data type. Arrays can be **fixed-size** or **dynamic-size**, and Solidity also supports **byte arrays** for efficient storage.

---

## 🔥 Types of Arrays in Solidity

### 1️⃣ **Fixed-Size Arrays**
- Declared with a predefined length.
- Cannot change its size after declaration.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FixedArrayExample {
    uint[5] public fixedArray = [1, 2, 3, 4, 5];

    function getElement(uint index) public view returns (uint) {
        return fixedArray[index];
    }
}
```

---

### 2️⃣ **Dynamic-Size Arrays**
- Does not have a predefined size.
- Can grow or shrink using `push()` and `pop()`.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DynamicArrayExample {
    uint[] public dynamicArray;

    function addElement(uint _value) public {
        dynamicArray.push(_value);
    }
    
    function removeLastElement() public {
        dynamicArray.pop();
    }

    function getLength() public view returns (uint) {
        return dynamicArray.length;
    }
}
```

---

### 3️⃣ **Byte Arrays**
- Used to store raw binary data.
- **`bytes`** is a dynamic byte array.
- **`bytes1` to `bytes32`** are fixed-size byte arrays.
- Cannot be modified directly; padding of `0` is added at the end if the value does not occupy the entire space.
- Stored in **hexadecimal format**.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ByteArrayExample {
    bytes public dynamicBytes = "hello";
    bytes4 public fixedBytes = 0x12345678;

    function getByte(uint index) public view returns (bytes1) {
        return dynamicBytes[index];
    }
}
```

---

## 🎯 Summary Table
| Array Type | Resizable? | Example |
|------------|------------|----------------|
| Fixed-Size Array | ❌ No | `uint[3] public arr;` |
| Dynamic-Size Array | ✅ Yes | `uint[] public arr;` |
| Byte Array | ✅ (dynamic) / ❌ (fixed) | `bytes public b;`, `bytes4 public b4;` |
