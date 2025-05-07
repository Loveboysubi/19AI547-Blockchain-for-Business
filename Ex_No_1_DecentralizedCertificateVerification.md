### Experiment 1: Decentralized Certificate Verification
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract CertificateVerification {
    address public university; 

    
    mapping(bytes32 => bool) public certificates;

    
    event CertificateIssued(bytes32 certHash);

    
    constructor() {
        university = msg.sender;
    }

   
    function issueCertificate(string memory studentName, string memory degree, uint year) public {
        require(msg.sender == university, "Only university can issue certificates");

        
        bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));

        certificates[certHash] = true;
        emit CertificateIssued(certHash);
    }

    
    function verifyCertificate(string memory studentName, string memory degree, uint year) public view returns (bool) {
        bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
        return certificates[certHash];
    }
}
'''
## Expected Output:
```
![Screenshot 2025-04-16 033730](https://github.com/user-attachments/assets/afef3e39-c82d-47fa-bed8-8618227706ea)
![Screenshot 2025-04-16 033703](https://github.com/user-attachments/assets/2536c182-18e0-49f6-9dad-c7342a1ccce6)


● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
## Result:
Thus, To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity is excuted successfully.
