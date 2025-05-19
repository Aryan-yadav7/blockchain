## 6. Create a contract that splits incoming Ether between 3 fixed addresses.

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract EtherSplitter {
    address payable public recipient1;
    address payable public recipient2;
    address payable public recipient3;

    constructor(address payable _addr1, address payable _addr2, address payable _addr3) {
        require(_addr1 != address(0) && _addr2 != address(0) && _addr3 != address(0), "Invalid address");
        recipient1 = _addr1;
        recipient2 = _addr2;
        recipient3 = _addr3;
    }

    receive() external payable {
        uint splitAmount = msg.value / 3;

        recipient1.transfer(splitAmount);
        recipient2.transfer(splitAmount);
        recipient3.transfer(msg.value - splitAmount * 2); // Last one gets the remainder if not divisible
    }

    function getContractBalance() public view returns (uint) {
        return address(this).balance;
    }
}
```

#Deployment
![ques6_1](https://github.com/user-attachments/assets/3f3b53d2-b104-43b9-8249-f7c7525575b7)
![ques6_2](https://github.com/user-attachments/assets/1a2a8474-a825-4074-8a77-209962d48ff7)

