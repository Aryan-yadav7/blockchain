## 5. Implement a simple auction system where users can place bids, and the highest bidder wins.

``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleAuction {
    address public highestBidder;
    uint public highestBid;

    function bid() public payable {
        require(msg.value > highestBid, "Bid too low");

        if (highestBid != 0) {
            payable(highestBidder).transfer(highestBid);
        }

        highestBidder = msg.sender;
        highestBid = msg.value;
}
}
```
#Deployment
![ques5_1](https://github.com/user-attachments/assets/2e3f347b-7052-4b94-9b30-6e01fa6102bb)
![ques5_2](https://github.com/user-attachments/assets/10696641-8283-400c-b243-6ae2b5164b85)
