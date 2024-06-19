# Best number Smart Contract
The Best number smart contract empowers users to designate and retrieve their PrimaryChoice. It comprises functions for number validation employing various error-management approaches (require(), assert(), and revert()).
## Description
The BestNumber smart contract is a Solidity-based Ethereum smart contract designed to give users a simple and secure way to set and retrieve their primary choice number. By leveraging the Ethereum blockchain, users can interact with the contract using their Ethereum wallets or through other smart contracts.

Users can use the setPrimaryChoice() function to specify their best number. The contract ensures the number provided is greater than zero, utilizing the require() statement for input validation.

The getPrimaryChoice() function allows users to retrieve the number they previously set as their primary choice. This function is read-only, ensuring that users can view their best number without changing the contract's state.

To demonstrate various error-handling mechanisms in Solidity, the contract includes additional functions like testAssert(), testRequire(), and testRevert(). These functions showcase the use of assert(), require(), and revert() statements.
## Getting Started

### Installing
To download the code, you can visit the following file path:-[ https://github.com/Anshulkoundal0101/eth-avax]
### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at ([https://remix.ethereum.org/.](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null))

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Meta.sol). Copy and paste the following code into the file:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract Bestnumber {
    uint private PrimaryChoice;

       // Function to set the PrimaryChoicer, but only if it's a positive integer!

    function setPrimaryChoice(uint _number) public {
        // Using require to check the number is greater than zero
        require(_number > 0, "Come on, my primarychoice can't be zero or negative!");
        PrimaryChoice = _number;
    }

    // Function to get the PrimaryChoice

    function getPrimaryChoice() public view returns (uint) {
        return PrimaryChoice;
    }

    // Function using assert to check a condition
    function testAssert() public view {
        // Using assert to ensure the PrimaryChoice is always greater than zero
        assert(PrimaryChoice > 0);
    }

    // Function using require to check a condition
  // Make sure I didn't accidentally set my favorite number to zero
    function testRequire() public view {
        // Using require to ensure the PrimaryChoice is greater than zero
        require(PrimaryChoice > 0, "PrimaryChoice should be greater than zero");
//"Oh no, my favorite number can't be zero!"
    }

    // Function using revert to check a condition
  // One last check to make sure everything is okay
    function testRevert() public view {
      // If this condition is true, we have a problem!
        // Using revert to check if the PrimaryChoice is zero
        if (PrimaryChoice == 0) {
            revert("PrimaryChoice should be greater than zero");
        }
    }
}
```
## Authors
Anshul koundal @Anshul_koundal_0101 (IG)
## License

This smart contract is licensed under the MIT License. See the LICENSE file for details.
