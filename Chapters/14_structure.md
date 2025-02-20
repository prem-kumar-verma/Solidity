# Structures in Solidity

## 📌 Introduction
In Solidity, a `struct` is a user-defined data type that allows grouping multiple related variables under a single entity. It is useful for organizing complex data structures in smart contracts.

---

## 🔥 1️⃣ **Declaring a Struct**
A `struct` is defined using the `struct` keyword, followed by the structure name and its attributes.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StructureExample {
    // Defining a struct
    struct Person {
        string name;
        uint age;
        bool isRegistered;
    }
}
```
🔹 In this example, `Person` contains three properties: `name` (string), `age` (uint), and `isRegistered` (bool).

---

## 🔥 2️⃣ **Using Structs in Solidity**
After declaring a struct, we can create instances and manipulate data.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StructureExample {
    struct Person {
        string name;
        uint age;
        bool isRegistered;
    }

    // Creating a person instance
    Person public person;

    // Function to set values
    function setPerson(string memory _name, uint _age, bool _isRegistered) public {
        person = Person(_name, _age, _isRegistered);
    }

    // Function to get person details
    function getPerson() public view returns (string memory, uint, bool) {
        return (person.name, person.age, person.isRegistered);
    }
}
```
🔹 `setPerson()` sets the values for a `Person` instance, while `getPerson()` retrieves them.

---

## 🔥 3️⃣ **Array of Structs**
Multiple struct instances can be stored in an array.

#### Example:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StructArray {
    struct Person {
        string name;
        uint age;
        bool isRegistered;
    }

    Person[] public people;

    function addPerson(string memory _name, uint _age, bool _isRegistered) public {
        people.push(Person(_name, _age, _isRegistered));
    }

    function getPerson(uint index) public view returns (string memory, uint, bool) {
        Person memory p = people[index];
        return (p.name, p.age, p.isRegistered);
    }
}
```
🔹 This contract maintains an array of `Person` structs, allowing multiple entries.

---

## 🎯 Summary Table
| Feature | Description |
|-----------------|-------------|
| `struct` | Defines a custom data type with multiple properties |
| Single Struct | Stores a single instance of a struct |
| Array of Structs | Manages multiple instances of a struct |
