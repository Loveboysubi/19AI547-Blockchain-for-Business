# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)
# Aim:
To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks.

# Algorithm:
Step 1: User Registration
A user registers with their Ethereum public key (instead of a password).


Step 2: Login Process
When logging in, the user signs a random challenge message using their private key.


The smart contract verifies the signature using the user’s public key.



# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PasswordlessAuth {
    mapping(address => bool) public registeredUsers;

    event UserRegistered(address user);
    event UserAuthenticated(address user);

    function registerUser() public {
        require(!registeredUsers[msg.sender], "Already registered");
        registeredUsers[msg.sender] = true;
        emit UserRegistered(msg.sender);
    }

    function authenticate(bytes32 hash, uint8 v, bytes32 r, bytes32 s) public view returns (bool) {
        require(registeredUsers[msg.sender], "User not registered");
        address signer = ecrecover(hash, v, r, s);
        return signer == msg.sender;
    }
}
```

# Expected Output:
Users can register without a password.
![WhatsApp Image 2025-04-28 at 14 56 40_04c2dbed](https://github.com/user-attachments/assets/bd954c59-b324-422c-8877-76c17e7a07c2)

![WhatsApp Image 2025-04-28 at 14 56 56_fa157411](https://github.com/user-attachments/assets/2859049e-7da5-487f-90cb-3a35fafff39d)

![WhatsApp Image 2025-04-28 at 14 56 54_1452fe31](https://github.com/user-attachments/assets/c3882f08-e04c-4f64-89ac-73389b79b225)

Users sign a challenge with their private key for authentication.

![WhatsApp Image 2025-04-28 at 14 56 56_ffa726ea](https://github.com/user-attachments/assets/39efef63-f718-49cc-b192-eae904629761)


# High-Level Overview:
Eliminates password hacks & phishing attacks.

Uses Ethereum's built-in cryptographic functions.


Inspired by Web3 login solutions like MetaMask authentication.

# RESULT: 
thus the program has been excuted successfully.
