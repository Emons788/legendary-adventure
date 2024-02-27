# legendary-adventure
Open
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract EmonToken {
    string public name = "Emon";
    string public symbol = "EMON";
    uint256 public totalSupply = 1000000; // Total supply of Emon tokens
    mapping(address => uint256) public balanceOf;

    event Transfer(address indexed from, address indexed to, uint256 value);

    constructor() {
        balanceOf[msg.sender] = totalSupply;
    }

    function transfer(address _to, uint256 _value) public returns (bool success) {
        require(balanceOf[msg.sender] >= _value, "Insufficient balance");
        require(_to != address(0), "Invalid recipient address");

        balanceOf[msg.sender] -= _value;
        balanceOf[_to] += _value;

        emit Transfer(msg.sender, _to, _value);
        return true;
    }
}
