# Mappings in Solidity

## 📌 Introduction
Mappings in Solidity are key-value data structures that store and retrieve data efficiently. They work like hash tables or dictionaries in other programming languages.

---

## 🔥 1️⃣ **Declaring a Mapping**
Mappings use the syntax `mapping(keyType => valueType)`. The `keyType` must be a built-in Solidity type (e.g., `address`, `uint`), while `valueType` can be any type, including structs and other mappings.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MappingExample {
    // Mapping from address to uint (balance storage)
    mapping(address => uint) public balances;
}
```
🔹 This creates a mapping where an Ethereum address maps to a `uint` value representing a balance.

---

## 🔥 2️⃣ **Using Mappings in Solidity**
Mappings allow storing, retrieving, and updating values efficiently.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MappingExample {
    mapping(address => uint) public balances;
    
    // Function to set balance
    function setBalance(address _user, uint _amount) public {
        balances[_user] = _amount;
    }
    
    // Function to get balance
    function getBalance(address _user) public view returns (uint) {
        return balances[_user];
    }
}
```
🔹 This contract allows setting and retrieving balances for specific addresses.

---

## 🔥 3️⃣ **Nested Mappings**
Mappings can also be nested to store more complex data structures.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract NestedMapping {
    mapping(address => mapping(string => uint)) public userBalances;

    function setUserBalance(address _user, string memory _token, uint _amount) public {
        userBalances[_user][_token] = _amount;
    }

    function getUserBalance(address _user, string memory _token) public view returns (uint) {
        return userBalances[_user][_token];
    }
}
```
🔹 This contract stores balances for multiple token types per user.

---

## 🎯 Important Notes
- **Mappings are not iterable**: You cannot iterate over keys or values.
- **Mappings do not return default values**: Unset values return the default value (e.g., `0` for `uint`).
- **Mappings are gas-efficient**: Since they are stored efficiently in the Ethereum Virtual Machine (EVM).
- **Cannot check existence**: Unlike arrays, mappings do not provide a way to check if a key exists.
