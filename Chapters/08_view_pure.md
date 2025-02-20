# View vs Pure in Solidity & Constructor Explanation

## 📌 View vs Pure Functions in Solidity

In Solidity, **view** and **pure** functions are used to specify functions that do not modify the blockchain state. However, they have key differences:

### 🔥 View Functions
- **Can read** state variables.
- **Cannot modify** state variables.
- Do not require gas when called externally.

#### Example of a View Function:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ViewExample {
    uint public num = 10;

    // View function: Reads state variable but does not modify it
    function getNum() public view returns (uint) {
        return num;
    }
}
```

### 🔥 Pure Functions
- **Cannot read or modify** state variables.
- Used for calculations that rely only on function arguments.
- Do not require gas when called externally.

#### Example of a Pure Function:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract PureExample {
    // Pure function: Does not access state variables
    function add(uint a, uint b) public pure returns (uint) {
        return a + b;
    }
}
```

---

## 📌 Constructor in Solidity
A **constructor** is a special function that is executed **only once**, at the time of contract deployment. It is used to initialize state variables.

### 🔥 Constructor Properties
- Executed **once** when the contract is deployed.
- Used to initialize state variables.
- Can accept parameters during deployment.

#### Example of a Constructor:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ConstructorExample {
    string public name;
    uint public age;

    // Constructor function
    constructor(string memory _name, uint _age) {
        name = _name;
        age = _age;
    }
}
```

### 🛠 Explanation:
- The constructor initializes `name` and `age`.
- When deploying the contract, values must be provided.

---

## 🎯 Summary Table
| Feature  | View Function | Pure Function | Constructor |
|----------|--------------|--------------|-------------|
| Reads State Variables | ✅ Yes | ❌ No | ✅ Yes |
| Modifies State Variables | ❌ No | ❌ No | ✅ Yes (during deployment) |
| Uses Arguments | ✅ Yes | ✅ Yes | ✅ Yes |
| Called Multiple Times | ✅ Yes | ✅ Yes | ❌ No (only once) |
