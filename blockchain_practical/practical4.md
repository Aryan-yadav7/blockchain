## 4. Write a contract where people can donate Ether and the top 3 donors are tracked

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DonationTracker {
    struct Donor {
        address donorAddress;
        uint amount;
    }

    mapping(address => uint) public totalDonated;
    Donor[3] public topDonors;

    event DonationReceived(address indexed donor, uint amount);
    event TopDonorsUpdated(address[3] topAddresses, uint[3] topAmounts);

    function donate() public payable {
        require(msg.value > 0, "Donation must be greater than zero");

        totalDonated[msg.sender] += msg.value;
        updateTopDonors(msg.sender, totalDonated[msg.sender]);

        emit DonationReceived(msg.sender, msg.value);
    }

    function updateTopDonors(address donor, uint newTotal) internal {
        // Check if donor is already in the top 3
        for (uint i = 0; i < 3; i++) {
            if (topDonors[i].donorAddress == donor) {
                topDonors[i].amount = newTotal;
                sortTopDonors();
                return;
            }
        }

        // If not in top 3, check if they qualify to enter
        for (uint i = 0; i < 3; i++) {
            if (newTotal > topDonors[i].amount) {
                topDonors[2] = Donor(donor, newTotal);
                sortTopDonors();
                return;
            }
        }
    }

    function sortTopDonors() internal {
        for (uint i = 0; i < 2; i++) {
            for (uint j = 0; j < 2 - i; j++) {
                if (topDonors[j].amount < topDonors[j + 1].amount) {
                    Donor memory temp = topDonors[j];
                    topDonors[j] = topDonors[j + 1];
                    topDonors[j + 1] = temp;
                }
            }
        }

        emit TopDonorsUpdated(
            [topDonors[0].donorAddress, topDonors[1].donorAddress, topDonors[2].donorAddress],
            [topDonors[0].amount, topDonors[1].amount, topDonors[2].amount]
        );
    }

    function getTopDonors() public view returns (address[3] memory, uint[3] memory) {
        address[3] memory addresses;
        uint[3] memory amounts;

        for (uint i = 0; i < 3; i++) {
            addresses[i] = topDonors[i].donorAddress;
            amounts[i] = topDonors[i].amount;
        }

        return (addresses, amounts);
    }
}
```

# Deployment
![ques4_1](https://github.com/user-attachments/assets/f52dc834-e2d8-446d-8e1b-5c4c90a715bb)
![ques4_2](https://github.com/user-attachments/assets/5e363a3d-f89c-43a7-ae8e-158d84a117c1)

