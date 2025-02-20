# Mapping in Structures in Solidity

## 📌 Introduction
In Solidity, **mappings** are key-value stores used for efficient data retrieval, while **structs** allow grouping multiple variables into a single type. By combining **mappings inside structs**, developers can create organized and easily accessible data structures for smart contracts.

---

## 🔥 **Mapping Inside Structs**
Mappings inside structs enable efficient storage and retrieval of structured data. This is particularly useful for scenarios like:
- **Managing user records**
- **Storing financial transactions**
- **Tracking product ownership**

### ✅ **Example of Mapping Inside a Struct**
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract EmployeeRecords {
    
    struct Employee {
        string name;
        uint age;
        string position;
    }
    
    mapping(address => Employee) public employees;
    
    function addEmployee(address _employeeAddress, string memory _name, uint _age, string memory _position) public {
        employees[_employeeAddress] = Employee(_name, _age, _position);
    }
    
    function getEmployee(address _employeeAddress) public view returns (string memory, uint, string memory) {
        Employee memory emp = employees[_employeeAddress];
        return (emp.name, emp.age, emp.position);
    }
}
```

### 🔹 **Explanation**
1. **Struct Definition (`Employee`)**: Holds employee details like `name`, `age`, and `position`.
2. **Mapping (`employees`)**: Maps an `address` to an `Employee` struct.
3. **Function `addEmployee()`**: Adds employee details to the mapping.
4. **Function `getEmployee()`**: Retrieves an employee's details by their address.

---

## 🔥 **Mapping Struct Inside Another Struct**
Sometimes, you may need to store multiple structured records under a single entity. This is done by **nesting mappings inside structs**.

### ✅ **Example of Nested Mapping in Structs**
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentGrades {
    struct Student {
        string name;
        mapping(string => uint) grades; // Mapping subject to marks
    }
    
    mapping(address => Student) students;
    
    function addStudent(address _studentAddress, string memory _name) public {
        students[_studentAddress].name = _name;
    }
    
    function addGrade(address _studentAddress, string memory _subject, uint _grade) public {
        students[_studentAddress].grades[_subject] = _grade;
    }
    
    function getGrade(address _studentAddress, string memory _subject) public view returns (uint) {
        return students[_studentAddress].grades[_subject];
    }
}
```

### 🔹 **Explanation**
1. **Nested Mapping (`grades`)**: Maps subjects to student grades inside the struct.
2. **Function `addStudent()`**: Initializes a student’s record.
3. **Function `addGrade()`**: Stores the grade for a subject.
4. **Function `getGrade()`**: Retrieves the grade for a specific subject.

---

## 📌 **Key Points to Remember**
1. **Mappings are reference types** – They store data efficiently.
2. **Mappings cannot be iterated** – Unlike arrays, they do not provide a way to loop through entries.
3. **Mappings inside structs enable efficient organization of data** – Ideal for user records, voting systems, and inventory tracking.
4. **Nested mappings provide deeper hierarchical storage** – Useful for multi-level data associations.
5. **Mappings cannot be returned from functions** – You can return individual elements but not the entire mapping.

---

## 🎯 **Conclusion**
Mappings inside structs allow **efficient storage, organization, and retrieval** of structured data in Solidity smart contracts. By leveraging nested mappings, developers can create hierarchical data structures for various applications.
