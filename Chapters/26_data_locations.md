# Data Locations in Solidity

## Introduction
In Solidity, data can be stored in three main locations: `storage`, `memory`, and `calldata`. Each of these locations has different properties regarding lifetime, cost, and mutability.

## Types of Data Locations

### 1. **Storage**
- **Lifetime:** Persistent (stored permanently on the blockchain).
- **Scope:** Used for state variables.
- **Cost:** High gas cost because changes are recorded on the blockchain.
- **Usage:** Used when data needs to be stored permanently.
- **Mutability:** Mutable (can be modified after being stored).
- **Example:**

```solidity
pragma solidity ^0.8.0;

contract StorageExample {
    uint256 public storedNumber; // Stored in storage

    function setNumber(uint256 _num) public {
        storedNumber = _num; // Modifies the storage variable
    }
}
```

### 2. **Memory**
- **Lifetime:** Temporary (exists only during function execution).
- **Scope:** Used for function parameters and temporary variables.
- **Cost:** Moderate gas cost (cheaper than `storage`).
- **Usage:** Used for temporary computations inside functions.
- **Mutability:** Mutable (can be modified within the function scope, but resets after function execution).
- **Example:**

```solidity
pragma solidity ^0.8.0;

contract MemoryExample {
    function getDouble(uint256 _num) public pure returns (uint256) {
        uint256 temp = _num * 2; // Stored in memory
        return temp;
    }
}
```

### 3. **Calldata**
- **Lifetime:** Limited to an external function call.
- **Scope:** Used for function parameters (cannot be modified).
- **Cost:** Lower gas cost compared to `memory`.
- **Usage:** Best for read-only function parameters in external calls.
- **Mutability:** Immutable (cannot be changed once assigned).
- **Example:**

```solidity
pragma solidity ^0.8.0;

contract CalldataExample {
    function getStringLength(string calldata _str) external pure returns (uint256) {
        return bytes(_str).length; // _str is stored in calldata and is immutable
    }
}
```

## **Comparison Table**

| Data Location | Lifetime | Scope | Cost | Modifiable? | Mutability |
|--------------|----------|-------|------|------------|------------|
| Storage | Permanent | State Variables | High | Yes | Mutable |
| Memory | Temporary (during function execution) | Function parameters & variables | Moderate | Yes | Mutable (within function scope) |
| Calldata | Temporary (only for external function calls) | Function parameters | Low | No | Immutable |

## **Key Takeaways**
- **Use `storage` for persistent data that needs to be saved on the blockchain.**
- **Use `memory` for temporary variables inside functions to save gas costs.**
- **Use `calldata` when passing immutable external function parameters to reduce gas usage.**
- **`storage` variables are mutable and persist on-chain, while `memory` variables are temporary and mutable within a function. `calldata` variables are immutable.**

Understanding these data locations helps in writing gas-efficient and optimized smart contracts in Solidity.
