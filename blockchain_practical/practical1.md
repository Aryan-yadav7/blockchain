## 1.Create a voting system with multiple candidates. Each address can vote only once.

# Voting Contract

```solidity
 // SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VotingSystem {
    struct Candidate {
        string name ;
        uint voteCount;
    }
    
    Candidate[] public candidates;
    mapping(address => bool) public hasVoted;
    
    // Constructor now clearly shows it needs an ARRAY of strings
    constructor(string[] memory _candidateNames) {
        for(uint i = 0; i < _candidateNames.length; i++) {
            candidates.push(Candidate({
                name: _candidateNames[i],
                voteCount: 0
            }));
        }
    }
```

# Deployment
![ques1_1](https://github.com/user-attachments/assets/98d08b02-9889-4da0-82d6-7942471c1e99)
![ques1_2](https://github.com/user-attachments/assets/99096eb8-018e-4866-a5d5-a089e2c46fbf)

