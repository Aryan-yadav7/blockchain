## 2. Write a contract that manages a list of student records (name, roll number). Allow adding and retrieving student data

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentRecords {
    struct Student {
        string name;
        uint rollNumber;
    }

    mapping(uint => Student) private students;
    uint[] private rollNumbers;

    event StudentAdded(string name, uint rollNumber);

    function addStudent(string memory _name, uint _rollNumber) public {
        require(students[_rollNumber].rollNumber == 0, "Roll number already exists.");

        students[_rollNumber] = Student(_name, _rollNumber);
        rollNumbers.push(_rollNumber);

        emit StudentAdded(_name, _rollNumber);
    }

    function getStudent(uint _rollNumber) public view returns (string memory name, uint rollNumber) {
        require(students[_rollNumber].rollNumber != 0, "Student not found.");

        Student memory s = students[_rollNumber];
        return (s.name, s.rollNumber);
    }

    function getAllRollNumbers() public view returns (uint[] memory) {
        return rollNumbers;
    }
}
```

#DEPLOYMENT
![ques2_1](https://github.com/user-attachments/assets/9e8f90b3-d70c-4f41-87b9-71b0b0646b27)
![ques2_2](https://github.com/user-attachments/assets/b212c8e8-01f2-4b25-a28d-b04e475c8194)

