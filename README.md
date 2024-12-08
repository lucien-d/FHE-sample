# FHE-sample
test sample
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FHEContract {

    uint256 public encryptedNumber1;
    uint256 public encryptedNumber2;
    uint256 public decryptedSum;

    constructor(uint256 _encryptedNumber1, uint256 _encryptedNumber2) {
        encryptedNumber1 = _encryptedNumber1;
        encryptedNumber2 = _encryptedNumber2;
    }

    function decryptAndAdd() public {
        uint256 decrypted1 = encryptedNumber1;
        uint256 decrypted2 = encryptedNumber2;

        decryptedSum = decrypted1 + decrypted2;
    }

    function getEncryptedData() public view returns (uint256, uint256) {
        return (encryptedNumber1, encryptedNumber2);
    }
}
