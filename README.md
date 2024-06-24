# himachal mla Smart Contract
The HimachalPradeshMLAs smart contract is a decentralized application on the Ethereum blockchain designed to manage and maintain a registry of Members of the Legislative Assembly (MLAs) for the state of Himachal Pradesh

## Description
The HimachalPradeshMLAs smart contract is designed to manage a registry of Members of the Legislative Assembly (MLAs) for the state of Himachal Pradesh. It allows the owner (admin) to add, update, deactivate, and retrieve MLA details. The contract also includes functions to demonstrate error-handling mechanisms in Solidity, such as assert(), require(), and revert() statements.

The HimachalPradeshMLAs contract is designed to be used by the contract owner to manage the list of MLAs. The owner can add new MLAs, update their constituencies, and deactivate them as needed. Users can retrieve the details of any MLA using their ID. 

The HimachalPradeshMLAs smart contract is a robust and secure solution for managing a registry of MLAs. By leveraging the Ethereum blockchain, it ensures transparency, security, and easy access to information, fostering greater trust and efficiency in the administrative processes.
## Getting Started

### Installing
To download the code, you can visit the following file path:-[ https://github.com/Anshulkoundal0101/eth-avax]
### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at ([https://remix.ethereum.org/.](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null))

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Meta.sol). Copy and paste the following code into the file:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract HimachalPradeshMLAs {
    struct MLA {
        string name;
        string constituency;
        bool isActive;
    }

    mapping(uint => MLA) private mlas; // Mapping of MLA IDs to MLA structs
    uint private mlaCount; // Counter for MLA IDs
    address private owner; // Owner of the contract (admin)

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Only the owner can perform this action");
        _;
    }

    // Function to add a new MLA
    function addMLA(string memory _name, string memory _constituency) public onlyOwner {
        require(bytes(_name).length > 0, "MLA name must not be empty");
        require(bytes(_constituency).length > 0, "MLA constituency must not be empty");
        mlaCount++;
        mlas[mlaCount] = MLA(_name, _constituency, true);
    }

    // Function to get MLA details
    function getMLA(uint _id) public view returns (string memory, string memory, bool) {
        require(_id > 0 && _id <= mlaCount, "MLA ID does not exist");
        MLA memory mla = mlas[_id];
        return (mla.name, mla.constituency, mla.isActive);
    }

    // Function to update MLA constituency
    function updateConstituency(uint _id, string memory _newConstituency) public onlyOwner {
        require(_id > 0 && _id <= mlaCount, "MLA ID does not exist");
        require(bytes(_newConstituency).length > 0, "New constituency must not be empty");
        mlas[_id].constituency = _newConstituency;
    }

    // Function to deactivate an MLA
    function deactivateMLA(uint _id) public onlyOwner {
        require(_id > 0 && _id <= mlaCount, "MLA ID does not exist");
        mlas[_id].isActive = false;
    }

    // Function using assert to check a condition
    function testAssert(uint _id) public view {
        MLA memory mla = mlas[_id];
        // Using assert to ensure the MLA's name is always not empty
        assert(bytes(mla.name).length > 0);
    }

    // Function using require to check a condition
    function testRequire(uint _id) public view {
        // Using require to ensure the MLA ID exists
        require(_id > 0 && _id <= mlaCount, "MLA ID does not exist");
    }

    // Function using revert to check a condition
    function testRevert(uint _id) public view {
        // Using revert to check if the MLA ID does not exist
        if (_id == 0 || _id > mlaCount) {
            revert("MLA ID does not exist");
        }
    }
}
```
## Authors
Anshul koundal @Anshul_koundal_0101 (IG)
## License

This smart contract is licensed under the MIT License. See the LICENSE file for details.
