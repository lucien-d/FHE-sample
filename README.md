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

from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP
import binascii

key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

cipher = PKCS1_OAEP.new(public_key)

number1 = 10
number2 = 20

encrypted_number1 = cipher.encrypt(str(number1).encode())
encrypted_number2 = cipher.encrypt(str(number2).encode())

decipher = PKCS1_OAEP.new(private_key)
decrypted_number1 = int(decipher.decrypt(encrypted_number1).decode())
decrypted_number2 = int(decipher.decrypt(encrypted_number2).decode())

result = decrypted_number1 + decrypted_number2
print(f"Decrypted Sum: {result}")
