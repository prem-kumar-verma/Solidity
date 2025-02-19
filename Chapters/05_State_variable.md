# State Variables in Solidity

## 📌 What are State Variables?
State variables are variables that are **declared at the contract level** and are stored **permanently in blockchain memory**. Unlike local variables, state variables persist beyond function execution.

### ⚡ Key Characteristics:
- Stored **permanently** in the blockchain (storage memory).
- Requires **gas fees** when modified.
- Storage is **not dynamically allocated**.
- If declared as `public`, Solidity **automatically generates a getter function**.
- Cannot be deleted; once deployed, they remain immutable unless explicitly changed by a function.

---

## 📌 Declaring a State Variable
A state variable is declared **inside the contract but outside any function**.

### **Example:**
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract State {
    // State variables (stored permanently on blockchain)
    uint public age = 10;
    // age = 10; Wrong method
    // Constructor to initialize state variables
    constructor() {
        age = 25;
    }
    
    // Function to update age (modifies state, requires gas fee)
    function setAge(uint _newAge) public {
        age = _newAge;
    }
    
}
```

---

## 📌 How to Initialize State Variables?
### **There are 3 ways to initialize state variables:**

1️⃣ **At the time of declaration**
```solidity
string public name = "Alice";
```
- The value is set when the contract is deployed.
- Consumes gas at deployment but avoids modifying state later.

2️⃣ **Using the constructor** *(Recommended for dynamic values)*
```solidity
constructor() {
    name = "Alice";
    age = 25;
}
```
- Constructor executes **only once** at deployment.
- Instance of the constructor **cannot** have other state variables beyond those declared.

3️⃣ **Using a setter function**
```solidity
function setAge(uint _newAge) public {
    age = _newAge;
}
```
- Allows updating state variables after contract deployment.
- Requires **gas fees** since it modifies blockchain storage.

---

## 📌 Important Points to Note 🚀
1. **Gas Fees:** State variable updates cost gas, so use them efficiently.
2. **Storage vs. Memory:** State variables use **storage memory**, unlike function variables that use **memory**.
3. **Immutable Variables:** Solidity allows declaring variables as `immutable`, meaning they can only be set once.
4. **Automatic Getter for Public State Variables:**
   - Declaring a state variable as `public` automatically generates a getter function.
   - Example: `uint public age;` allows `age()` to be called externally.
5. **State Variables in View/Pure Functions:**
   - `view` functions **can read** state variables but **cannot modify** them.
   - `pure` functions **cannot read or modify** state variables.

---

## 🎯 Summary
- **State variables store permanent data** on the blockchain.
- **Gas fees apply** when modifying them.
- **Public state variables automatically generate getters**.
- **They can be initialized in 3 ways**: at declaration, inside the constructor, or using setter functions.
- **Constructor variables must match declared state variables**.
