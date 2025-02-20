# Visibility in Solidity

## 📌 Introduction
Visibility in Solidity determines who can access functions and state variables within a smart contract. There are four types of visibility:

1. **Public** – Accessible by anyone (both internally and externally).
2. **Private** – Accessible only within the same contract.
3. **Internal** – Accessible within the same contract and derived contracts.
4. **External** – Accessible only from outside the contract.

---

## 🔥 **Types of Visibility and Their Differences**

| Visibility  | Access Within Contract | Access by Derived Contracts | Access Externally | Access Internally |
|------------|-----------------------|----------------------------|-------------------|------------------|
| Public     | ✅ Yes                 | ✅ Yes                      | ✅ Yes             | ✅ Yes           |
| Private    | ✅ Yes                 | ❌ No                       | ❌ No              | ❌ No            |
| Internal   | ✅ Yes                 | ✅ Yes                      | ❌ No              | ✅ Yes           |
| External   | ❌ No                  | ❌ No                       | ✅ Yes             | ❌ No            |

---

## ✅ **Example Code: Demonstrating Visibility in Solidity**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VisibilityExample {
    string public publicVar = "I am Public";   // Accessible from everywhere
    string private privateVar = "I am Private"; // Accessible only within this contract
    string internal internalVar = "I am Internal"; // Accessible within this and derived contracts

    function publicFunction() public view returns (string memory) {
        return "Public Function Called";
    }

    function privateFunction() private pure returns (string memory) {
        return "Private Function Called";
    }

    function internalFunction() internal pure returns (string memory) {
        return "Internal Function Called";
    }

    function externalFunction() external pure returns (string memory) {
        return "External Function Called";
    }
    
    // Trying to call different functions within the contract
    function testFunctions() public view returns (string memory, string memory) {
        string memory test1 = publicFunction(); // ✅ Can call public function
        // string memory test2 = privateFunction(); // ❌ Cannot call private function
        string memory test3 = internalFunction(); // ✅ Can call internal function
        // string memory test4 = externalFunction(); // ❌ Cannot call external function internally
        return (test1, test3);
    }
}

contract Derived is VisibilityExample {
    function testDerived() public view returns (string memory) {
        return internalFunction(); // ✅ Can access internal function from derived contract
    }
}
```

---

## 📌 **Key Takeaways**
1. **Public** – Accessible from anywhere, inside and outside the contract.
2. **Private** – Accessible only inside the same contract.
3. **Internal** – Similar to `private`, but also accessible by derived contracts.
4. **External** – Can be accessed only from outside the contract, not internally.

---

## 🎯 **Conclusion**
Understanding function and variable visibility is essential for writing secure and efficient Solidity smart contracts. Choosing the right visibility ensures that contract logic remains protected while allowing necessary interactions.
