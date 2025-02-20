# Address and Reference Data Types in Solidity

## 📌 Introduction
Solidity provides different data types, including **value types** and **reference types**. 

### ✅ **Key Categories Covered**:
1. **Address Data Type** – Stores Ethereum addresses.
2. **Reference Data Types** – Includes **strings, arrays, mappings, and structs**.

---

## 🔥 **Address Data Type**
An `address` in Solidity holds a 20-byte Ethereum address. It comes in two types:
- **address**: A plain Ethereum address.
- **address payable**: An address that can receive Ether payments.

### Example Code:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract AddressExample {
    address public owner; // Regular address
    address payable public recipient; // Payable address

    constructor() {
        owner = msg.sender; // Assign contract deployer as owner
    }

    function setRecipient(address payable _recipient) public {
        recipient = _recipient;
    }

    function sendEther() public payable {
        require(msg.value > 0, "Send some Ether");
        recipient.transfer(msg.value);
    }
}
```
### **Explanation:**
- `owner`: Stores the deployer's address.
- `recipient`: Holds a payable address.
- `setRecipient()`: Assigns a new recipient.
- `sendEther()`: Transfers Ether to `recipient`.

---

## 🔥 **Reference Data Types**
Reference data types store dynamic data and need memory management.

### **1️⃣ Strings** (Sequence of characters)
```solidity
contract StringExample {
    string public greeting = "Hello, Solidity!";

    function updateGreeting(string memory _newGreeting) public {
        greeting = _newGreeting;
    }
}
```
**Key Points:**
- **Stored in memory/storage**.
- **Strings are mutable** (can be updated).
- **Operations like concatenation require additional logic**.

---

### **2️⃣ Arrays** (Fixed & Dynamic)
```solidity
contract ArrayExample {
    uint[] public numbers; // Dynamic Array
    uint[5] public fixedNumbers; // Fixed Size Array

    function addNumber(uint _num) public {
        numbers.push(_num);
    }

    function getNumber(uint _index) public view returns (uint) {
        return numbers[_index];
    }
}
```
**Key Points:**
- Fixed-size arrays have predefined length.
- Dynamic arrays can grow or shrink.
- Use `.push()` to add elements.

---

### **3️⃣ Mappings** (Key-Value Pair Storage)
```solidity
contract MappingExample {
    mapping(address => uint) public balances;

    function setBalance(uint _amount) public {
        balances[msg.sender] = _amount;
    }
    function getBalance(address _addr) public view returns (uint) {
        return balances[_addr];
    }
}
```
**Key Points:**
- **Mappings store data as key-value pairs.**
- **Efficient for lookups but cannot be iterated.**
- **Default value for non-existing keys is 0.**

---

### **4️⃣ Structs** (Custom Data Structures)
```solidity
contract StructExample {
    struct User {
        string name;
        uint age;
    }

    mapping(address => User) public users;

    function createUser(string memory _name, uint _age) public {
        users[msg.sender] = User(_name, _age);
    }
}
```
**Key Points:**
- **Structs group related data together.**
- **Useful for complex data storage.**
- **Can be used with mappings for user records.**

---

## 🎯 **Key Takeaways**
- `address` is used to store Ethereum addresses, with `address payable` for Ether transactions.
- **Reference types** store complex data like strings, arrays, mappings, and structs.
- **Strings are mutable, arrays can be fixed or dynamic.**
- **Mappings store key-value pairs and are efficient for lookups.**
- **Structs allow defining custom data types.**

🚀 **Use these data types effectively to structure smart contracts efficiently!**
