# Solidity Sample Code: Identity Contract

## 📌 Solidity Smart Contract Example
Below is a simple Solidity smart contract named **Identity**:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Identity {
    string name;
    uint age;
    
    // Constructor to initialize name and age
    constructor() public {
        name = "Ravi";
        age = 17;
    }
    
    // Function to return the name
    function getName() public view returns (string memory) {
        return name;
    }
    
    // Function to return the age
    function getAge() public view returns (uint) {
        return age;
    }
    
    // Function to increment the age
    function setAge() public {
        age = age + 1;
    }
}
```

---

## 🔥 Explanation of the Code
### **1. SPDX License Identifier**
- `// SPDX-License-Identifier: MIT` is used to specify the license type for the contract. This helps in ensuring compliance and transparency.

### **2. Pragma Directive**
- `pragma solidity ^0.8.0;` ensures that the contract will be compiled with Solidity version **0.8.0 or later**, but not breaking changes.

### **3. Contract Declaration**
- `contract Identity {}` defines a new smart contract named `Identity`.

### **4. State Variables**
- `string name;` stores a **name** (data type: `string`).
- `uint age;` stores an **age** (data type: `uint`).

### **5. Constructor**
- The **constructor** initializes values when the contract is deployed:
  ```solidity
  constructor() public {
      name = "Ravi";
      age = 17;
  }
  ```
  - `name` is set to **"Ravi"**.
  - `age` is set to **17**.
  - The constructor executes **only once** at contract deployment.

### **6. Functions to Get and Update Data**
#### **Function: `getName()`**
```solidity
function getName() public view returns (string memory) {
    return name;
}
```
- `view` means it **does not modify** the blockchain state.
- `returns (string memory)` specifies the return type.
- **Returns** the `name` variable ("Ravi").

#### **Function: `getAge()`**
```solidity
function getAge() public view returns (uint) {
    return age;
}
```
- Returns an **unsigned integer (`uint`)**, representing age.

#### **Function: `setAge()`**
```solidity
function setAge() public {
    age = age + 1;
}
```
- This function **increments** the age by 1 each time it is called.
- It modifies the contract's state, so it does not use `view` or `pure`.
- Useful in scenarios where the age needs to be updated dynamically.

---

## 🔗 Return Type Explanation
| Function | Return Type | Description |
|----------|------------|-------------|
| `getName()` | `string memory` | Returns a string (stored in memory) |
| `getAge()` | `uint` | Returns an unsigned integer |
| `setAge()` | No return | Modifies state, increments age by 1 |

- The return type **indicates the type of data** the function will return.
- In the function itself, the `return` statement shows the **variable name** being returned.

---

## 🔥 Compilation and Auto-Compilation in Remix
### **1. Compile Option in Remix**
- In the **Remix IDE**, the **Compile** button compiles Solidity code into **bytecode** and **ABI**.
- Errors and warnings appear if there are any issues.

### **2. Auto-Compilation in Remix**
- The **Auto Compile** option automatically compiles the contract whenever you make changes.
- Recommended for **quick debugging and testing**.

---

## 🎯 Conclusion
- This contract stores **name and age**, allows users to retrieve them, and increments the age dynamically.
- Solidity is **statically typed and case-sensitive**.
- **Remix IDE** makes it easy to compile and test contracts.
- **Understanding return types** helps in working with smart contract functions.

