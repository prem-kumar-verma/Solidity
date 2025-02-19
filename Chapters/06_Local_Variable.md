# Local Variables in Solidity

## 📌 What are Local Variables?
Local variables are variables **declared inside a function** and are **temporary** in nature. They **exist only during function execution** and are **not stored permanently** in the blockchain.

### ⚡ Key Characteristics:
- Stored **in the stack** (not blockchain storage).
- **Do not require gas fees** (unless interacting with state variables).
- Exist only within the function where they are declared.
- **Cannot have visibility specifiers** (`public`, `private`, etc.).
- **Storage keywords (`storage`, `memory`) cannot be used at the contract level**.

---

## 📌 Example: Using Local Variables
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Local {
    function store() pure public returns (uint) {
        uint age = 10; // Local variable (stored in stack, not blockchain storage)
        string memory name = "Ravi"; // Local string variable stored in memory
        return age; // Returns age, but name is not returned since it is not used
    }
}
```

---

## 📌 Explanation of the Code
1. **Function store()**:
   - Defined as `pure`, meaning it does not modify or read state variables.
   - It declares two **local variables**: `age` (uint) and `name` (string memory).
   - `uint age = 10;` → Stored in the **stack**, exists only during function execution.
   - `string memory name = "Ravi";` → Since strings are dynamic, `memory` is required.
   - **Only `age` is returned**, as `name` is unused.

---

## 📌 Important Points 🚀
1. **No Gas Fees:** Local variables do **not** consume blockchain storage, so they don’t require gas fees.
2. **Lifetime:** They are **temporary** and destroyed after the function executes.
3. **Storage vs. Memory vs. Stack:**
   - `stack` → Local variables (like `uint age`) are stored in the stack (efficient & fast).
   - `memory` → Used for dynamic variables (like `string memory name`), not stored permanently.
   - `storage` → For state variables, stored permanently in blockchain.
4. **Reference Types:**
   - Solidity requires specifying `memory` for reference types (like strings, arrays, structs) inside functions.
   - `storage` cannot be used inside a function.
5. **Cannot be Accessed Outside the Function:**
   - Unlike state variables, local variables **cannot be accessed globally**.

---

## 🎯 Summary
- **Local variables exist only within functions**.
- **Stored in stack/memory, not blockchain**.
- **Do not require gas unless interacting with state variables**.
- **`memory` must be specified for dynamic data types**.
- **Cannot be used outside the function where they are declared**.
