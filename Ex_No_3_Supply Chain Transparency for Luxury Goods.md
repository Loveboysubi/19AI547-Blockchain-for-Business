# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
Step 1:
A project owner starts a campaign with a funding goal and deadline.

Step2:
Contributors can send ETH to the campaign.

Step3:
If the goal is met before the deadline, funds are released to the project owner.

Step4:
If the goal is not met, contributors can withdraw their funds.

# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.

![Screenshot 2025-04-16 095444](https://github.com/user-attachments/assets/c1999292-bebd-4632-9baf-8acd01f429cb)
Ownership is transferred at every checkpoint.
![Screenshot 2025-04-16 095704](https://github.com/user-attachments/assets/fa8b1857-f9b4-4b2f-92b3-da64c934d48e)

# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 
Thus, To Develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity is excutted successfully.
