## 3. Develop a contract that only allows the deployer (owner) to call a specific function (use modifiers).

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract OwnerOnly {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the contract owner");
        _;
    }

    string private secretMessage;

    function setSecret(string memory _message) public onlyOwner {
        secretMessage = _message;
    }

    function getSecret() public view returns (string memory) {
        return secretMessage;
    }
}
```

![ques3_1](https://github.com/user-attachments/assets/acb87c1e-a086-4867-8e6e-29f7cdff9d8a)
![ques3_2](https://github.com/user-attachments/assets/fda2860a-dc0e-4e1d-8a70-6a26169f5aff)
